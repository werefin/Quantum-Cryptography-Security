# Quantum Cryptography & Security: lab reports

## About this project

* **Lab 01 (QRNG)**: implementation of two types of QRNG, characterized by different degrees of trust on their elements. For the trusted QRNG setup, the first set of data is used to estimate the classical min-entropy for both the mixed state and the pure D state. For the Source-Device-Independent QRNG, instead, the first and second sets of data are used to calculate the quantum conditional min-entropy using the entropic uncertainty principle for both the mixed state and the pure D state. Moreover, the first and second sets of data are also used to calculate the quantum conditional min-entropy using the tomographic method for both the mixed state and the pure D state, assuming $S_{2}=0$ due to the lack of full tomographic measurements. Indeed, the third set of data is used to calculate the quantum conditional min-entropy for the L state using both the entropic uncertainty principle and the tomographic method. Using the min-entropies estimated from these steps, the security parameter from the leftover hashing lemma (LHL) is analyzed to see how it changes as a function of the block length;
  
* **Lab 02 (QKD IR)**: analysis of error correction (EC) implementation for QKD using LDPC codes. The Python source code and LDPC codes, hosted on [GitHub](https://github.com/marcoavesani/QKD_LDPC_python). During the session, we modified several parameters in the script and library files to understand their impact on EC:
  * **Changing QBER values**: we varied the QBER from 0.01 to 0.1. The software calculated the optimal base code rate and the optimal number and position of puncturing and shortening bits. We analyzed how the base rate, efficiency, number of iterations, and the number of puncturing and shortening bits changed as a function of the QBER;
  * **Fixed base rate with varying QBER**: we selected three QBER values (0.01, 0.05, 0.09) and fixed the base rate of the LDPC code. The software calculated the optimal number of shortening and puncturing bits for each scenario. We analyzed how the efficiency, number of iterations, and the number of puncturing and shortening bits changed as a function of the QBER;
  * **Efficiency definition**: we introduced the standard definition of efficiency $f_1 = \lambda_{EC} \ / \ n_z \cdot h_2(E_z)$, where $\lambda_{EC}$ is the number of disclosed bits, $n_z$ is the number of generated bits in the key basis, and $h_2(E_z)$ is the binary entropy of the QBER in the key basis. We discussed why this measure does not always correctly quantify the actual efficiency of error correction, especially at low QBER.

  Then, using the code analyzed during the lab session, we manually changed the number of shortening and puncturing bits for data with different QBER values in two cases: deterministic number of   errors & BSC channel and analyzed how the efficiency and the number of iterations are affected. We also implemented a different error correction procedure ([Cascade](https://link.springer.com/content/pdf/10.1007/3-540-48285-7_35.pdf)), tested it, and evaluated the efficiency as a function of the QBER, comparing it to the LDPC case. Finally, we compared the efficiencies obtained with both the standard definition of efficiency $f_1$ and another efficiency measure $f_2 = \lambda_{EC} \ / \ n_z - h_2(E_z)$;

* **Lab 03 (QKD)**: the dataset includes three files of raw keys:
  - `input-keys.alice`: Alice's choices of basis and state;
  - `input-keys.decoy`: Alice's choices of decoy state;
  - `input-keys.bob`: Bob's detected states.

  These raw keys are obtained from a Quantum Key Distribution (QKD) run after synchronization and discarding of unreceived qubits. Please refer to the report for details regarding encoding and decoding procedures. The protocol employed is the 3-state 1-decoy efficient BB84 protocol, with clearly defined parameters as specified in the pdf. Using the provided dataset, we estimate the Quantum Bit Error Rate (QBER) in both bases and Secret Key Rate (SKR) as a function of time. The main focus was on estimating SKR using appropriate block sizes and security parameters to account for finite size effects. Full classical post-processing steps such as Error Correction or Privacy Amplification are not required for this estimation.
