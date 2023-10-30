# Task Group: Attached Matrix Facility

## Proposed charter
Matrix operations are a key operation in deep-learning training and inference for workloads like natural-language processing, recommendation systems, and image recognition.  With the pervasive use of these applications in environments ranging from the datacenter, through IoT to mobile applications, matrix operations for RISC-V should scale across these application domains and apply to high-performance and resource-constrained environments.

The Matrix Operations Unit TG will specify an attached Matrix Operations Unit Extension.  An attached matrix unit executes instructions that are part of the processor instruction stream and, from an architectural perspective, must follow program order. An attached matrix unit is also self-contained and orthogonal to other architectural resources: it defines its own set of matrix registers and uses these as part of its specified operations. 

The Matrix Operations Unit will specify an extension to the RISC-V ISA that implements a scalable (i.e., with the ability to operate on different operand sizes and allow the writing of matrix-geometry agnostic code) matrix operations unit. This matrix operations unit will be a standalone block implementable without dependencies on the RISC-V Vector extension.

The resulting specification will encompass:
- an overview of the commonly used matrix operations in established algorithms and commonly used software libraries;
- a specification of the architectural state capable of holding/referencing two-dimensional matrix tiles of configurable/variable geometry;
- a specification of those matrix operations supported as part of this extension, including at least:
	- load, store, and move operations
		- between memory and the matrix tile architectural state
		- (if implemented together with the RISC-V Vector extension) between RISC-V vector registers and rows/columns of the matrix tile architectural state
	- matrix-matrix, vector-matrix and scalar-matrix arithmetic operations
	- matrix permutation operations
	- sparse-matrix compression/decompression;
- a predication mechanism to control operations performed on matrix tiles;
- a mapping of matrix operations onto instructions defined in the (newly defined) Matrix Operations Extension; and
- a review of the interactions of matrix load/store and prefetching of matrices with the RISC-V memory models and a specification of any deviations from the standard RISC-V memory model.

## Acting leadership
- Qiu Jing (Alibaba)
- Philipp Tomsich (VRULL)

## Proposed workplan
1. Inception (1 month) : Preliminary charter, call-for-candidates and identification of experts/resources
1. Requirements analysis (4 months)
1. Specification development (6 months)
1. Proof-of-concept and quantitative analysis (6 months)

## Proposed deliverables

### Specification deliverables
- Matrix operations unit extensions
- Intrinsics specification for matrix operations

### Compatibility and simulation tools
- SAIL
- Hand-written ACT w/ coverage-analysis

### Proof-of-concept implementations
- Linux kernel (e.g., context switching for matrix tiles)
- TensorFlow
- oneDNN (https://github.com/oneapi-src/oneDNN)
- GNU binutils
- GCC with intrinsics support
- QEMU
- LLVM MLIR
