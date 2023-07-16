### Install
```
pip install python-protobuf
```

### Example
```py
from pyproto import Protobuf

print("Test the conversion between protobuf and bytes")
bs = bytes.fromhex("12001a0022020801") # A section of bytes data of protobuf
print("src:", bs.hex())
proto = ProtoBuf(bs)  # Convert bytes to protobuf objects
proto.dump()  # print proto object
bs2 = proto.toBuf()  # Convert the proto object to bytes
print(bs2 == bs, bs2.hex())

print("Mutual conversion between proto object and dict object")
# A complex dict object

d = {
    6: {
        1: {
            1: "eyJhbGciOiJIUzI1NiJ9.ODYxODAyNjMyNjcwMA.KGj7v_WjlntNODpPNe4fVbJA5sPhLjZbQidBLhcrGVM"
        },
        3: "5******7@*****.com",
        4: {1: 6},
        5: {1: 1},
        6: {2: "", 3: "", 4: {1: 1}},
    }
}

# An unassigned dict object template

d2 = {6: {1: {1: ""}, 3: "", 4: {1: 0}, 5: {1: 0}, 6: {2: "", 3: "", 4: {1: 0}}}}
print("src:", d)
pb = ProtoBuf(d)  # Convert dict object to protobuf object

pb.dump()

d3 = pb.toDict(d2)  # Convert protobuf object to dict object

print("d3 == d2 ->", d3 == d2, d3 is d2, d3)
print("d3 == d  ->", d3 == d, d3 is d)
```