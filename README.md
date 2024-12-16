# tick_data_compression


https://github.com/lemire/FastPFor/tree/master

https://www.timescale.com/blog/time-series-compression-algorithms-explained

https://ethw.org/History_of_Lossless_Data_Compression_Algorithms?ref=timescale.ghost.io

**Integer compression:**

- Delta encoding
- Delta-of-delta encoding
- Simple-8b
- Run-length encoding

**Floating point compression:**

- XOR-based compression

**Data-agnostic compression:**

- Dictionary compression


# Repo structure

1. Download ITCH data
  https://emi.nasdaq.com/ITCH/Nasdaq%20ITCH/
2. Decode ITCH
   https://github.com/amankrx/matching-engine-rs
4. Save to duckdb parquet
5. In per ticker partition, apply compression using duckdb UDF
6. Compare before-compression, general compression and sophiscated compreesion result

Integer: 
1) `delta_encoding | simple_8b`
2) `delta_encoding | simple_8b | rle `
3) `simple_8b`

Float:
1) `to_integer | delta_encoding | simple_8b | rle`
2) `xor_compression`

TickerName:
1) `to_dictionary`
