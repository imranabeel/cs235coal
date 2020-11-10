# CS235: Lecture 3


## Intoduction to Memory modes
<!--- 
> <img src="memory modes.png" width="400" height="300" />
--->

> <img src="memory model page.png"  />

____
# Protected Mode Memory Addressing:
> Segment register contains a selector that selects a descriptor from the descriptor table.
> The descriptor contains information about the segment, e.g., it's base address, length and access rights.
> The offset can be 32-bits.

> <img src="Protected Mode Memory Addressing.gif"  />

## Segment Descriptors in Protected Mode:

> <img src="Segment Descriptors in Protected Mode.gif"  />

## Segment Registers in Protected Mode:
> The 13 bit descriptor index selects one of up to 8K descriptors in either the GDT and LDT, as specified by the TI bit.

>> Therefore, these 14 bits allows access to 16K 8-byte descriptors.

> <img src="Segment Registers in Protected Mode.gif"  />

## Segmentation Address Translation:
> + Programmer invisible registers:
>> - The other registers enclosed by the red-dotted line are part of the descriptor cache.
>>> * The cache is used to reduce the number of actual memory references needed to construct the physical address.
 

>> - There is one cache register for each of the 6 segment registers, CS, DS, etc. and the LDTR (Local Descriptor Table Register) and TR (Task Register) selectors.
 

>>> * The base address, limit and access rights of the descriptor are loaded from memory every time the corresponding selector changes.
 

>> - The LDTR and TR selectors refer to special system descriptors in the GDT.

>>> * These registers provide hardware acceleration support for task switching.
 

>> - Let's first consider how LDTs are used to extend the address space of individual tasks.

> <img src="Segmentation Address Translation.gif" /> 

## Segmentation Address Translation:
> <img src="Segmentation Address Translation2.gif" /> 



## Local Descriptor Tables:
The LDTR selector indexes a GDT system descriptor describing the segment containing the LDT while the cache stores the actual LDT descriptor.
> <img src="Local Descriptor Tables.gif" /> 
> 


____


# 80286 protected mode example: 

> <img src="Overlapping_realmode_segments.svg"/>

# Paging and Virtual Memory:

> <img src="Paging and Virtual Memory.gif"/>

# Paging address translation:

> <img src="paging_address_translation.gif"/>


# Reference: 
<http://ece-research.unm.edu/jimp/310/slides/micro_arch2.html>