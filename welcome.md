# Welcome!

C++ can feel overwhelming!

Maybe you first encountered it in CS2040C algorithms & data structures module. Maybe you heard horror stories about pointers and seemingly mysterious segmentation faults that span 300 lines!

Despite its pitfalls, C++ remains the language of choice behind the many of the world's fastest systems. This includes high performance databases like [Clickhouse](https://clickhouse.com/) and [RocksDB](https://rocksdb.org/), game engines like [Unreal Engine](https://www.unrealengine.com/en-US/unreal-engine-5) and browsers like [Google Chrome](https://www.google.com/intl/en_sg/chrome/).&#x20;

In this guide, I'll be gently introducing modern C++, walk through some common pitfalls and together we'll look at some of C++ most powerful features!

### Why C++?

Unlike purely managed languages, C++ does not shy away from the messy details. Instead, it forces one to understand what your program is actually doing. This includes understanding how memory layout, object lifetimes and resource management actually works.  While this might appear initially uncomfortable, it helps builds deep intuition about how computers actually work.



### Using This Guide

This guide aims to:

✅ Build strong intuition around memory, ownership, and RAII\
✅ Help you write modern C++ (C++17/20 style) instead of legacy C-with-classes\
✅ Explain _why_ things work, not just _how_ to use them\
✅ Connect C++ concepts to real systems (networking, trading systems, performance engineering)

This guide does **not**:

❌ Try to cover every corner of the language specification, for that, please refer to the official [C++ reference](https://cppreference.com/)\
❌ Encourage unsafe practices for the sake of cleverness\
❌ Claim that C++ is definitely the best tool for every problem

### Who Am I?

I'm Benn Tan, a computer science undergraduate from the National University of Singapore and a core member of NUS Hackers.

I enjoy building high-performance systems, exploring low-latency engineering, and understanding what happens under the hood — from hash maps and allocators to networking stacks and distributed systems.

Over time, I’ve come to appreciate C++ not just as a language, but as a way to think about performance, control, and abstraction.

This guide is a consolidation of the mental models I wish I had earlier.
