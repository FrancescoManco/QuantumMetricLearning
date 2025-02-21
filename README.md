# Quantum Triplet Loss + KMeans

## Overview
This project explores a **hybrid quantum-classical architecture** for **embedding generation and clustering**, leveraging **Quantum Triplet Loss** and **KMeans**. The model integrates **classical CNNs, quantum circuits, and a triplet loss framework** to extract and refine image embeddings. The pipeline is tested on the **MNIST dataset (digits 0-9)** to evaluate clustering performance.

## Model Architecture
The approach combines:
- A **Siamese network** for embedding generation, using an **anchor-positive-negative triplet**.
- **Classical CNN layers** for feature extraction.
- **Dimensionality reduction** to an 8-dimensional feature space.
- **Quantum circuit processing** via a layer with TorchConnector:

## Initial Quantum Circuit
- Encoding: **yz_angles_encoding**
- Ansatz: **RealAmplitudes layers on 4 qubits**
- Final measurement: **full qubit sampling** to generate feature distributions.

## Results on MNIST (0-9)
| Model Variant | Purity | Silhouette |
|--------------|--------|------------|
| **Hybrid (CNN + Quantum)** | **0.905** | **0.547** |
| **Quantum Triplet Loss V2** | **0.868** | **0.689** |

### Encoding Variants:
| Encoding | Purity | Silhouette |
|----------|--------|------------|
| **HRyRx** | 0.896 | 0.495 |
| **HRyRz** | 0.849 | 0.455 |
| **RyRx** | 0.780 | 0.424 |
| **HRyRz + Normalization** | 0.842 | 0.377 |

### Ansatz Variants (RyRz Encoding):
| Ansatz | Purity | Silhouette |
|--------|--------|------------|
| **MPS** | 0.904 | 0.457 |
| **MPS + TTN** | 0.885 | 0.463 |
| **CMPS** | 0.784 | 0.391 |
| **CTTN** | 0.885 | 0.494 |

## Usage
1. Train the embedding model using **Triplet Loss**.
2. Extract embeddings from **Quantum and Classical Networks**.
3. Apply **KMeans** clustering and evaluate **Silhouette & Purity** scores.

## Future Improvements
- Experimenting with **alternative ansatz structures**.
- Optimizing the **quantum encoding strategies**.
- Extending to more complex datasets beyond MNIST.
