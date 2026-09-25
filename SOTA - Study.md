Absolutely. I went through the uploaded paper, **“A Survey on State-of-the-art Deep Learning Applications and Challenges”** by Mohd Halim Mohd Noor and Ayokunle Olalekan Ige. The paper is a **survey/review paper**, not a paper proposing one new deep-learning algorithm. Its main purpose is to organize the development of deep learning—from fundamentals and architectures to modern applications and unresolved challenges. 

# 1. First: What is this paper actually about?

The easiest way to understand the whole paper is:

> **Deep Learning fundamentals → Major model families → Modern applications → Problems with current models → Future research**

The authors argue that previous surveys often concentrated on either DL architectures, CNNs, applications, or learning strategies separately. They position this paper as a broader survey that combines fundamentals, state-of-the-art applications, model characteristics, challenges, and future directions. 

The paper covers:

| Part          | What you learn                                               |
| ------------- | ------------------------------------------------------------ |
| **Section 1** | Why deep learning matters and what gap this survey addresses |
| **Section 2** | Neural-network fundamentals                                  |
| **Section 3** | Types of deep-learning models and CNN architectures          |
| **Section 4** | State-of-the-art applications                                |
| **Section 5** | Research challenges                                          |
| **Section 6** | Trends and future directions                                 |
| **Section 7** | Overall conclusion                                           |

The authors searched literature using databases including IEEE Xplore, ScienceDirect, SpringerLink, ACM Digital Library, Scopus and arXiv, followed by manual reference screening. 

---

# 2. ⭐ What you should understand first

Do **not** try to memorize every model mentioned in this paper.

There are a few ideas that form the backbone of the whole paper.

## ⭐ 2.1 Deep learning automatically learns features

This is one of the most important ideas.

Traditional machine learning often follows:

**Raw data → Feature engineering → ML algorithm → Prediction**

Deep learning tries to do:

**Raw data → Multiple neural-network layers → Learned representations → Prediction**

The authors explain this as hierarchical feature learning. Early layers can learn primitive patterns such as edges and lines, later layers combine them into increasingly complex representations. 

### Why this matters

This explains why CNNs are so effective for images.

Instead of manually telling the model:

> “Look for edges, corners, textures and shapes.”

the network learns useful representations from the training data.

**⭐ This concept is worth understanding very well because it explains much of the motivation behind deep learning.**

---

# 3. ⭐ Section 2 — Fundamentals of Deep Learning

This is one of the sections I would **definitely study**, particularly if you are using this paper for a thesis or literature review.

The authors cover layers, attention, activation functions, optimization/loss functions, and regularization. 

---

## ⭐ 3.1 Neuron and forward propagation

The paper starts with the basic neuron.

Essentially:

$$
z = \sum_j w_jx_j
$$

then

$$
a=g(z)
$$

where:

* \(x\) = input
* \(w\) = learned weight
* \(z\) = weighted sum
* \(g\) = activation function
* \(a\) = activation/output

The paper explicitly presents this formulation and then generalizes it to successive layers. 

### Why you should care

Everything later—CNN, RNN, LSTM, Transformer, etc.—ultimately builds on this basic operation.

**⭐ Must understand.**

---

# 4. ⭐ CNNs

CNNs are another major theme.

The important idea isn't simply:

> “CNN is used for images.”

It is:

> **CNN exploits local structure and weight sharing.**

Instead of every neuron connecting to every input, a convolutional neuron looks at a local region. The same weights are reused across different locations. 

This gives CNNs two major advantages:

**Local feature extraction**

and

**Parameter sharing**

The paper explains that this reduces the number of parameters and allows the same feature detector to work in different spatial locations. 

---

## ⭐ 4.1 Pooling

Pooling reduces spatial dimensions.

Typical examples:

* Max pooling
* Average pooling

The paper notes that pooling reduces feature-map size, reduces parameters and can provide translation-invariant features. 

### Important conceptual progression

Understand this:

**Input image**

↓

**Convolution**

↓

**Feature maps**

↓

**Pooling**

↓

**More convolution/pooling**

↓

**High-level representation**

↓

**Classification**

That is much more important than memorizing a particular filter size.

---

# 5. ⭐ Attention mechanisms — VERY IMPORTANT

I would mark this as one of the **highest-priority sections in the entire paper**.

The basic problem is:

> Not every part of the input is equally important.

The paper describes attention as a mechanism that dynamically assigns different importance/weights to different features. 

The authors discuss:

* Channel attention
* Temporal attention
* Self-attention
* Spatial attention
* Vision Transformer attention

---

## ⭐ Self-attention

This is particularly important.

The paper describes the standard procedure:

**Input embeddings**

↓

**Query, Key, Value**

↓

**Query-Key similarity**

↓

**Scaling**

↓

**Softmax**

↓

**Attention weights**

↓

**Weighted values**

The authors identify self-attention as a fundamental building block of Transformers. 

### This connects directly to:

* Transformers
* BERT
* modern NLP
* Vision Transformers
* many modern multimodal systems

So don't treat "attention" as just another small subsection.

**⭐ This is one of the key bridges between classical deep learning and modern architectures.**

---

# 6. ⭐ Activation functions

The paper discusses:

### Sigmoid

$$
0 < \sigma(x) < 1
$$

### Tanh

$$
-1 < \tanh(x) < 1
$$

### ReLU

$$
ReLU(x)=\max(0,x)
$$

The important issue is the **vanishing-gradient problem**.

Sigmoid and tanh can suffer from gradients becoming very small when networks become deep, making learning difficult. ReLU became important partly because it is computationally efficient and helps mitigate this problem. 

The paper also mentions ReLU variants such as:

* Leaky ReLU
* SiLU
* ELU

### ⭐ What to understand

Don't merely memorize definitions.

Understand this relationship:

**Deep network**

→ gradients propagate backward

→ gradients can become extremely small

→ early layers learn poorly

→ architectures/activations/residual connections were developed to alleviate the problem.

That idea appears repeatedly throughout the paper.

---

# 7. ⭐ Optimization and loss functions

The paper describes gradient descent as the mechanism for updating weights to reduce prediction error. 

The basic update is:

$$
w \leftarrow w-\alpha\nabla_wJ
$$

where:

* \(w\) = parameter
* \(\alpha\) = learning rate
* \(J\) = loss
* \(\nabla_wJ\) = gradient

The paper distinguishes:

### Batch gradient descent

All training examples contribute to an update.

### Stochastic gradient descent

One example at a time.

### Mini-batch gradient descent

A subset of examples.

The authors describe mini-batch training as a compromise between computational efficiency and gradient noise. 

They also discuss improvements such as momentum and adaptive learning rates. 

---

# 8. ⭐ Regularization

The paper covers:

* Early stopping
* Dropout
* L1/L2 penalties
* Weight decay
* Batch normalization
* Layer normalization

The overarching issue is:

> **Overfitting**

The model performs well on training data but poorly on unseen data. 

### Key conceptual relationship

**Too much model capacity + insufficient/diverse data**

→ overfitting

Regularization tries to improve **generalization**.

---

# 9. ⭐ Section 3 — Types of Deep Learning Models

This section explains the major model families.

## Supervised learning

The paper highlights:

* MLP
* CNN
* RNN

## Unsupervised learning

It discusses:

* Restricted Boltzmann Machines
* Deep Belief Networks
* Autoencoders
* Variational Autoencoders
* GANs

The supervised/unsupervised distinction is explicitly described in the paper.  

---

# 10. ⭐ RNN → LSTM → GRU

This evolution is important.

RNNs are designed for sequential data and maintain an internal state from previous time steps. 

But standard RNNs have difficulty learning long-term dependencies because of gradient problems.

This motivated:

### LSTM

Uses:

* forget gate
* input gate
* output gate
* cell state

### GRU

Uses:

* reset gate
* update gate

and has a simpler structure than LSTM. 

### ⭐ What you should remember

The important story is:

**RNN**

→ difficulty with long dependencies

→ **LSTM/GRU**

→ gating mechanisms

→ better long-term dependency learning.

---

# 11. ⭐ CNN architecture evolution

This paper gives a useful historical progression.

You should understand the **reason each architecture was introduced**, rather than memorizing architecture details.

### LeNet

Early CNN success.

↓

### AlexNet

Major ImageNet breakthrough.

↓

### VGG

Much deeper network using small \(3\times3\) filters.

↓

### GoogleNet/Inception

Parallel filters / multi-scale feature extraction.

↓

### ResNet

Residual/skip connections.

↓

### DenseNet

Dense feature reuse.

↓

### WideResNet

Increase width rather than relying only on depth.

↓

### ResNeXt

Increase cardinality/parallel transformation paths.

The paper discusses these developments and the problems they attempted to solve. 

---

# 12. ⭐ The most important CNN evolution: the problem → solution relationship

This is a great thing to put into your literature review.

| Problem                              | Architectural response        |
| ------------------------------------ | ----------------------------- |
| Deep networks difficult to train     | **Highway Network**           |
| Vanishing gradients                  | **ResNet / skip connections** |
| Feature reuse issues                 | **DenseNet**                  |
| Depth-related limitations            | **WideResNet**                |
| More diverse feature transformations | **ResNeXt**                   |
| Multi-scale features                 | **Inception**                 |

This is far more academically useful than saying:

> “ResNet is better than VGG.”

The literature-review question is:

> **What limitation existed, and what architectural innovation addressed it?**

---

# 13. ⭐ ResNet is particularly important

The paper explains that ResNet uses skip/residual connections so information can bypass intermediate layers. This helps with vanishing gradients and feature reuse. 

Conceptually:

$$
y=F(x)+x
$$

rather than forcing the network to learn the entire transformation directly.

**⭐ Definitely understand this.**

---

# 14. Autoencoders and GANs

The paper then moves into unsupervised/generative models.

## Autoencoder

Basic structure:

**Input**

↓

**Encoder**

↓

**Latent representation**

↓

**Decoder**

↓

**Reconstructed input**

The latent representation can be used for things such as dimensionality reduction and representation learning. 

The paper also introduces:

* Sparse autoencoder
* Contractive autoencoder
* Denoising autoencoder
* Variational autoencoder

---

## GAN

GAN has two networks:

**Generator**

and

**Discriminator**

The generator produces synthetic samples while the discriminator tries to distinguish real from generated samples. 

The paper also discusses:

* Conditional GAN
* InfoGAN
* WGAN
* ProGAN
* StyleGAN

### ⭐ Key problem

**Mode collapse**

The generator may produce only a limited variety of outputs.

WGAN and other architectures attempt to improve GAN training and quality. 

---

# 15. ⭐ Section 4 — State-of-the-art applications

This is the core application-oriented portion of the paper.

The authors organize modern applications around areas such as:

**Computer Vision**

**Natural Language Processing**

**Time Series Analysis**

**Pervasive Computing**

**Robotics**

The abstract explicitly identifies these domains as the primary application areas reviewed. 

---

# 16. ⭐ Computer Vision

The paper discusses:

* Image classification
* Object detection
* Image segmentation
* Image generation

A key historical point is the transition from early CNNs such as LeNet to AlexNet and later architectures. AlexNet's 2012 ImageNet result is described as a transformative milestone. 

The survey then describes more modern attention/Transformer-based approaches.

---

# 17. ⭐ Vision Transformers

This is another **must-read topic**.

The paper explains that ViT treats an image as a sequence of non-overlapping patches and uses self-attention to model relationships between them. 

The central advantage is:

> **Global relationships can be modeled directly.**

But there is an important limitation:

> ViTs can struggle with local spatial features and smaller datasets.

The paper therefore highlights hybrid architectures combining CNNs and Transformers, including Conformer and MaxViT. 

### ⭐ Literature-review insight

There is a broader architectural trend:

**CNN → Transformer → CNN + Transformer hybrid**

because researchers are trying to combine:

**CNN = local inductive bias**

with

**Transformer = global context**

That is a very useful point to carry into your literature review.

---

# 18. ⭐ NLP

The paper discusses NLP tasks such as:

* Text classification
* Machine translation
* Text generation
* Question answering
* Dialogue systems

The important architectural transition is toward **Transformers**.

The paper identifies Transformer architectures such as BERT and its variants as central to modern NLP applications, including classification, translation and generation. 

---

# 19. ⭐ Time-series analysis

This section is particularly interesting because the paper shows that different domains do **not** necessarily converge on exactly the same architecture.

For time series, the survey discusses approaches involving:

* CNNs
* RNNs
* LSTM
* GRU
* attention
* hybrid architectures

The paper observes that Transformers have progressed rapidly in computer vision and NLP, but time-series applications face challenges involving sequence structure, long sequences and limited dataset availability. Hybrid CNN/RNN/attention architectures therefore remain important. 

### ⭐ Important research insight

Do not assume:

> “Transformer is newer, therefore Transformer is always better.”

The paper actually demonstrates a more nuanced argument:

> **Architecture suitability depends on the structure and constraints of the problem.**

That's an excellent literature-review observation.

---

# 20. ⭐ Pervasive computing

This includes applications involving things such as:

* Human Activity Recognition
* wearable/sensor data
* ECG
* EEG
* IoT-type systems

The paper emphasizes that these systems often need **real-time processing** and may operate on resource-constrained devices. 

This creates an important tension:

**Higher model complexity**

vs.

**Real-time / low-resource deployment**

---

# 21. ⭐ Robotics

The robotics portion moves beyond simple prediction toward embodied intelligence.

The survey highlights issues including:

* Object identification
* Navigation
* Human-robot interaction
* multimodal perception
* LLM-based robotics

The authors specifically discuss LLMs for human-robot interaction and argue that future systems need better grounding, real-time processing and navigation capabilities. 

They also describe multimodal robotics, where systems combine information such as visual observations, internal robot state and planning information. 

---

# 22. ⭐ Section 5 — Research Challenges

This is arguably the **most valuable section for writing a literature review**, because this is where the paper stops saying:

> “Deep learning is successful.”

and starts asking:

> **“What is still wrong with it?”**

The authors organize challenges into:

### Ethical issues

### Technical issues

### Domain-specific issues



---

# 23. ⭐ Explainability / interpretability

One of the biggest challenges is the **black-box nature** of deep learning.

The authors note that complex models with many layers and parameters can be difficult to understand and explain, particularly in high-stakes areas such as healthcare. 

They discuss approaches including:

* Feature visualization
* Saliency maps
* Heatmaps
* Model distillation
* Intrinsically interpretable models

### ⭐ Why this matters

High predictive accuracy isn't necessarily enough.

A medical practitioner may need to know:

> **Why did the model make this diagnosis?**

rather than simply:

> **What diagnosis did it make?**

This is a major research direction.

---

# 24. ⭐ Bias and fairness

The paper discusses bias as another major ethical issue.

Bias can originate from:

**Training data**

→ **Training process**

→ **Final model**

The authors discuss mitigation at multiple stages, including changing the training data, adding fairness-related terms to the loss function, and post-processing the trained model. 

### ⭐ Important literature-review point

This shows that model performance cannot be evaluated only using overall accuracy.

A model can have high overall performance while behaving differently across subgroups.

---

# 25. ⭐ Computational cost

This is one of the biggest technical challenges.

As models become larger:

**Parameters ↑**

→ computation ↑

→ memory ↑

→ training time ↑

→ deployment difficulty ↑

The problem becomes especially important for:

* smartphones
* IoT devices
* embedded systems
* wearables
* robotic systems

The paper specifically recommends lightweight architectures and model compression. 

---

# 26. ⭐ Model compression

The paper identifies several approaches:

### Pruning

Remove unnecessary parameters/connections.

### Quantization

Represent weights/activations with lower precision.

### Knowledge distillation

Transfer knowledge from a large teacher model to a smaller student model.



This gives you another important research pattern:

**Large accurate model**

→ difficult deployment

→ **compression**

→ smaller efficient model

---

# 27. ⭐ Data scarcity

Another central problem:

> Deep learning generally benefits from large amounts of data.

But collecting high-quality labeled data can be expensive and may require domain experts. Poor-quality or biased data can consequently affect model performance. 

The paper proposes or discusses techniques such as:

* Transfer learning
* Self-supervised learning
* Data augmentation
* Synthetic data
* Active learning

---

# 28. ⭐ Self-supervised learning

This is a particularly important modern direction.

Instead of manually labeling everything:

**Unlabeled data**

↓

**Construct pretext task**

↓

**Model generates learning signal from data itself**

↓

**Learn representation**

↓

**Fine-tune for downstream task**

The paper explains that self-supervised learning can exploit large quantities of unlabeled data, which are often much easier and cheaper to obtain than labeled datasets. 

**⭐ Definitely mark this.**

---

# 29. ⭐ Adversarial attacks

This is one of the most important security-related concepts in the paper.

The basic idea:

> A tiny modification to an input can cause a deep-learning model to make a drastically different prediction.

The authors note that adversarial attacks can affect not only images but also text, signals, audio and video. 

This creates a major problem for systems deployed in:

* healthcare
* cybersecurity
* autonomous vehicles
* robotics
* surveillance

---

# 30. ⭐ What the authors see as the future

The final sections provide a useful map of where DL research could go.

The authors group future directions around several themes.

## Architecture

More hybrid:

**CNN + Transformer**

architectures.

## Data

Greater use of:

**self-supervised learning**

and synthetic/data-generation techniques.

## NLP

More:

* external knowledge
* domain-specific representations
* long-context interaction
* multimodal systems



## Time series

More:

* lightweight Transformers
* real-time processing
* hardware acceleration
* synthetic data
* personalization



## Robotics

More:

* multimodal perception
* real-time inference
* robust navigation
* LLM-grounded robotics



---

# 31. ⭐ One of the most interesting final arguments

The authors go beyond simply saying:

> “Make neural networks bigger.”

They suggest a future involving combinations of:

**Deep learning**

*

**Symbolic reasoning**

*

**Causal inference**

*

**Common sense**

This leads toward **neuro-symbolic AI**. 

They also mention:

* quantum computing
* neuromorphic computing
* multimodal intelligence

as possible longer-term directions. 

---

# 32. Literature Review — ready-to-use version

Below is a literature-review section you could adapt for an academic report/thesis.

## Literature Review: Deep Learning Applications, Architectures, and Challenges

Deep learning has emerged as a major data-driven approach within artificial intelligence because of its ability to automatically learn hierarchical representations from raw data. Unlike conventional machine-learning approaches that often depend on manually engineered features, deep neural networks learn increasingly complex representations through multiple processing layers. This capability has enabled deep learning to address complex problems across areas including computer vision, natural language processing, healthcare, time-series analysis, pervasive computing, and robotics. Noor and Ige describe this progression as a shift from manually designed feature representations toward hierarchical representation learning within deep neural networks. 

The foundations of modern deep learning are based on neural-network layers, nonlinear activation functions, optimization, loss functions, attention mechanisms, and regularization. A neural network performs a weighted transformation of its inputs followed by an activation function, while multiple layers enable increasingly complex representations to be learned. Convolutional layers extend this principle by exploiting local structure and weight sharing, making them particularly effective for image and other structured data. Pooling operations further reduce spatial dimensions and computational requirements. 

Attention mechanisms represent an important development in deep learning because they allow models to assign different levels of importance to different components of their input. The survey discusses channel, temporal, spatial, and self-attention mechanisms. In particular, self-attention forms the foundation of Transformer architectures by computing relationships between elements of a sequence using query, key, and value representations.  This development has had a major influence on subsequent research in natural language processing and computer vision.

Deep-learning architectures have evolved partly in response to limitations encountered in earlier models. Recurrent neural networks were designed for sequential data but can experience difficulties in learning long-term dependencies because of gradient-related problems. LSTM and GRU architectures introduced gating mechanisms to improve information retention and processing over long sequences.  Similarly, CNN architectures evolved from early models such as LeNet and AlexNet toward deeper and more sophisticated architectures including VGG, Inception, ResNet, DenseNet, WideResNet, and ResNeXt. These developments addressed issues including vanishing gradients, feature reuse, computational efficiency, and multi-scale representation learning. 

A major transition in recent deep-learning research has been the increased use of Transformer-based architectures. In computer vision, Vision Transformers represent images as sequences of patches and apply self-attention to capture relationships between distant image regions. However, the survey notes that Vision Transformers can have difficulties exploiting local spatial information and may be sensitive to dataset size and hyperparameters. Consequently, hybrid architectures such as Conformer and MaxViT have been developed to combine the local feature extraction capabilities of convolutional networks with the global-context modeling of Transformers. 

Natural language processing has similarly shifted toward Transformer-based models. The survey identifies BERT and related architectures as important foundations for contemporary NLP applications, including text classification, machine translation, and text generation. Future research identified by the authors includes integrating external knowledge bases, domain-specific representations, improved context updating, longer-context interaction, and multimodal processing. 

In contrast, time-series analysis demonstrates that the adoption of newer architectures depends strongly on the characteristics of the data and application. While Transformers have become dominant in computer vision and NLP, time-series applications continue to make substantial use of CNNs, recurrent neural networks, and attention-based hybrid architectures. The survey attributes this difference to challenges involving sequence structure, sequence length, dataset size, and data availability.  This suggests that architectural novelty alone does not determine suitability; rather, model selection must account for the structural characteristics and operational constraints of the target problem.

Despite substantial progress, the literature identifies several unresolved challenges. One major issue is the requirement for large and diverse datasets. Deep-learning models may overfit when training data are insufficient, while collecting and annotating high-quality domain-specific datasets can be expensive and time-consuming. Data collection can also introduce errors and bias. The survey therefore highlights transfer learning, self-supervised learning, synthetic data generation, and related approaches as potential solutions. 

Another important challenge is the computational cost of increasingly large models. Large parameter counts increase training time, memory requirements, and inference costs and can restrict deployment on resource-constrained devices. Model compression techniques such as pruning, quantization, and knowledge distillation are therefore important research directions for developing efficient models without substantially sacrificing predictive capability. 

Ethical and security concerns are equally important. Deep-learning systems can behave as black boxes, making their decisions difficult to interpret in high-stakes environments. Explainability methods, including feature visualization, saliency maps, heatmaps, and model distillation, have therefore become important for improving transparency and trust.  In addition, biased training data can produce discriminatory model behavior, leading to research on data-level, training-level, and post-processing approaches for bias mitigation. 

Security presents another unresolved issue because deep-learning models can be susceptible to adversarial attacks. Small perturbations to inputs can cause significant changes in predictions, and such vulnerabilities extend beyond image classification to text, audio, signals, and video. This creates particular risks when deep-learning systems are deployed in medical, security, and autonomous applications. 

Overall, the reviewed literature indicates a broad shift in deep learning from increasingly deep standalone architectures toward attention-based, hybrid, efficient, multimodal, and more data-efficient systems. The survey concludes that future progress is likely to involve combinations of convolutional and Transformer architectures, self-supervised learning, lightweight models, multimodal intelligence, and methods that integrate deep learning with symbolic reasoning and causal approaches.  

---

# 33. ⭐ What I would mark in the paper

Here is my recommended priority system.

### 🔴 MUST READ CAREFULLY

**Section 2.2 — Attention Mechanisms**

Especially:

* self-attention
* Query/Key/Value
* spatial attention
* temporal attention
* Vision Transformer

**Section 3.1.2 — RNN/LSTM/GRU**

Especially:

* vanishing gradients
* gating
* long-term dependencies

**Section 3.1.3 — CNN architectures**

Especially the progression:

**AlexNet → VGG → Inception → ResNet → DenseNet → WideResNet → ResNeXt**

**Section 4 — State-of-the-art applications**

Especially the transition from CNN/RNN toward Transformers and hybrid architectures.

**Section 5 — Research Challenges**

This is extremely important for a literature review:

* Explainability
* Bias
* Data scarcity
* Computational cost
* Adversarial attacks
* Deployment constraints

**Section 6 — Summary and Future Directions**

This is especially useful when writing your **research gap/future work**.

---

### 🟠 READ FOR UNDERSTANDING

**Section 2.1 — Layers**

Understand the fundamentals, but don't spend excessive time memorizing notation.

**Section 2.3 — Activation functions**

Know sigmoid, tanh, ReLU and why vanishing gradients matter.

**Section 2.4 — Optimization**

Understand gradient descent, mini-batch learning and learning-rate adaptation.

**Section 2.5 — Regularization**

Understand why dropout, weight decay, batch normalization, etc. are used.

**Section 3.2 — Autoencoders/GANs**

Understand the architecture and purpose rather than memorizing every variant.

---

### 🟢 SKIM

The many individual application papers cited in the survey.

You don't need to deeply study every one of the hundreds of references merely to understand this survey.

Instead, identify:

> **Problem → Model → Innovation → Advantage → Limitation**

That is the pattern you should extract.

---

# 34. The most useful way to take notes

For every important paper/model mentioned, make a table like this:

| Paper/Model              | Problem                       | Proposed approach            | Main advantage                       | Limitation                             |
| ------------------------ | ----------------------------- | ---------------------------- | ------------------------------------ | -------------------------------------- |
| AlexNet                  | Image classification          | Deep CNN + ReLU              | Major ImageNet improvement           | Large model                            |
| ResNet                   | Training very deep networks   | Residual connections         | Better gradient flow                 | Increasing complexity                  |
| DenseNet                 | Feature reuse                 | Dense connections            | Strong feature reuse                 | Computationally expensive              |
| ViT                      | Global image relationships    | Self-attention over patches  | Global context                       | Smaller-data limitations               |
| LSTM                     | Long-term sequence dependency | Gated recurrent cells        | Better long-term dependency learning | More complex                           |
| Transformer              | Sequence relationships        | Self-attention               | Global dependency modeling           | Computational cost                     |
| Self-supervised learning | Lack of labels                | Pretext/self-generated tasks | Uses unlabeled data                  | Representation quality/task dependence |

This format will be **much more valuable for your literature review** than simply writing paragraphs describing models.

---

# 35. The biggest research story in this paper

The entire paper can essentially be reduced to this evolution:

```text
Traditional ML
      ↓
Manual Feature Engineering
      ↓
Deep Neural Networks
      ↓
CNN / RNN
      ↓
Deeper Architectures
      ↓
Residual / Dense Connections
      ↓
Attention Mechanisms
      ↓
Transformers
      ↓
Hybrid CNN + Transformer Models
      ↓
Multimodal / Large Models
      ↓
Efficient + Explainable + Robust AI
```

And simultaneously:

```text
More powerful models
        ↓
More data required
        ↓
More computation required
        ↓
Deployment problems
        ↓
Explainability / fairness / security problems
        ↓
Research into:
efficient models
self-supervised learning
robustness
explainability
multimodality
hybrid architectures
```

**That second chain is especially important for identifying a research gap.**

---

# 36. One critical point about using this paper in your literature review

Don't write your literature review as:

> “The authors discussed CNN. Then they discussed RNN. Then they discussed Transformers. Then they discussed robotics.”

That becomes a **summary of the paper**, not a literature review.

Instead, use the paper to build an argument:

> Earlier architectures addressed representation learning for particular data structures, but increasing model depth introduced optimization difficulties. Residual and dense connectivity addressed information-flow and feature-reuse problems. Attention mechanisms subsequently enabled models to selectively emphasize relevant information, leading to Transformer-based architectures. However, the adoption of Transformers has introduced new challenges involving computational cost, data requirements, local feature extraction, and deployment efficiency. Consequently, recent research increasingly investigates hybrid, lightweight, self-supervised, robust, and multimodal architectures.

That is a **literature review argument**, because it connects studies through **problems, solutions, limitations, and research trends**, rather than merely listing them.

One final note: this particular survey is dated as a July 2025 preprint in the uploaded version, so its “state-of-the-art” claims should be treated as a snapshot of the literature available through that period, rather than as a definitive description of the DL field in 2026. 
