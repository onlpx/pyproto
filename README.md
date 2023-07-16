# pyproto
 Python Protobuf

```py
from pyproto import Protobuf

print("测试protobuf与bytes互相转换")
bs = bytes.fromhex("12001a0022020801")  # 一段protobuf的bytes数据
print("src:", bs.hex())
proto = ProtoBuf(bs)  # 将bytes转为protobuf对象
proto.dump()  # 打印proto对象
bs2 = proto.toBuf()  # 将proto对象转换成bytes
print(bs2 == bs, bs2.hex())

print("proto对象与dict对象的互相转换")
# 一个复杂的dict对象
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

# 一个未赋值的dict对象模板
d2 = {6: {1: {1: ""}, 3: "", 4: {1: 0}, 5: {1: 0}, 6: {2: "", 3: "", 4: {1: 0}}}}
print("src:", d)
pb = ProtoBuf(d)  # 将dict对象转换成protobuf对象
pb.dump()

d3 = pb.toDict(d2)  # 将protobuf对象转换成dict对象
print("d3 == d2 ->", d3 == d2, d3 is d2, d3)
print("d3 == d  ->", d3 == d, d3 is d)
```