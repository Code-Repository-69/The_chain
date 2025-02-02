import hashlib

def hashGenerator(data):  # Corrected function name
    result = hashlib.sha256(data.encode())
    return result.hexdigest()

class Block:
    def __init__(self, data, hash, prev_hash):
        self.data = data
        self.hash = hash
        self.prev_hash = prev_hash

class RupeeChain:
    def __init__(self):
        hashLast = hashGenerator('Last_gen')  # Correct reference to the function
        hashFirst = hashGenerator('First_gen')
        genesis = Block('gendata', hashLast, hashFirst)  # Use the correct class name (Block)
        self.chain = [genesis]

    def add_block(self, data):
        prev_hash = self.chain[-1].hash
        hash = hashGenerator(data + prev_hash)
        block = Block(data, hash, prev_hash)
        self.chain.append(block)

# Create a blockchain and add blocks
blch = RupeeChain()
blch.add_block('A')
blch.add_block('B')
blch.add_block('C')

# Print details of all blocks in the chain
for block in blch.chain:
    print(block.__dict__)

    
