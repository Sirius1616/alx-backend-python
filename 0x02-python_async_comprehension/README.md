0x02. Python - Async Comprehension

PEP 530 – Asynchronous Comprehensions
Author:
Yury Selivanov <yury at edgedb.com>
Discussions-To:
Python-Dev list
Status:
Final
Type:
Standards Track
Created:
03-Sep-2016
Python-Version:
3.6
Post-History:
03-Sep-2016
Table of Contents
Abstract
PEP 492 and PEP 525 introduce support for native coroutines and asynchronous generators using async / await syntax. This PEP proposes to add asynchronous versions of list, set, dict comprehensions and generator expressions.

Rationale and Goals
Python has extensive support for synchronous comprehensions, allowing to produce lists, dicts, and sets with a simple and concise syntax. We propose implementing similar syntactic constructions for the asynchronous code.

To illustrate the readability improvement, consider the following example:

result = []
async for i in aiter():
    if i % 2:
        result.append(i)
With the proposed asynchronous comprehensions syntax, the above code becomes as short as:

result = [i async for i in aiter() if i % 2]
The PEP also makes it possible to use the await expressions in all kinds of comprehensions:

result = [await fun() for fun in funcs]
