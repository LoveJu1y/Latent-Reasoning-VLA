title：Latent Reasoning VLA: Latent Thinking and Prediction for Vision-Language-Action Models

authors：
Shuanghao Bai * 1 2 Jing Lyu * 2 3 Wanqi Zhou 1 Zhe Li 2 Dakai Wang 1 Lei Xing 1 Xiaoguang Zhao 3
Pengwei Wang 2 Zhongyuan Wang 2 Cheng Chi 2 Badong Chen 1 Shanghang Zhang 2

institude：
*Equal contribution 1
Institute of Artificial Intelli￾gence and Robotics, Xi’an Jiaotong University. 2Beijing
Academy of Artificial Intelligence. 3University of Chinese
Academy of Sciences. 4
Peking Univeristy. Correspondence
to: Cheng Chi <chicheng@baai.ac.cn>, Badong Chen
<chenbd@mail.xjtu.edu.cn>, Shanghang Zhang <shanghang@pku.edu.cn>.

Abstract：

VisionLanguageAction (VLA) models benefit
from chainofthought (CoT) reasoning, but existing approaches incur high inference overhead
and rely on discrete reasoning representations that
mismatch continuous perception and control. We
propose Latent Reasoning VLA (LaRA-VLA), a
unified VLA framework that internalizes multi￾modal CoT reasoning into continuous latent rep￾resentations for embodied action. LaRA-VLA
performs unified reasoning and prediction in la￾tent space, eliminating explicit CoT generation
at inference time and enabling efficient, action￾oriented control. To realize latent embodied rea￾soning, we introduce a curriculum-based training
paradigm that progressively transitions from ex￾plicit textual and visual CoT supervision to la￾tent reasoning, and finally adapts latent reason￾ing dynamics to condition action generation. We
construct two structured CoT datasets and evaluate LaRAVLA on both simulation benchmarks
and longhorizon realrobot manipulation tasks.
Experimental results show that LaRAVLA consistently outperforms stateoftheart VLA methods while reducing inference latency by up to
90% compared to explicit CoTbased approaches,
demonstrating latent reasoning as an effective and
efficient paradigm for real-time embodied control

1. Model Architecture:

![model]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\2.png"),

![attention]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\4.png"),

（这两张图像并排放置）
 Training proceeds in three stages: (i) explicit CoT finetuning with aligned visual prediction latents
and inversedynamics supervision for actions; (ii) a curriculumbased transition from explicit CoT to compact text latents, gradually
reducing the number of text tokens while increasing reliance on latent reasoning, where the latent representations are also implicitly
supervised by visual and action signals; and (iii) adaptation of latentconditioned VLM features to an action expert for efficient action
generation without explicit CoT at inference time


2. Experiments

- Simulation Experiments

![Libero]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\3.png"),

On LIBERO, LaRA-VLA achieves the best overall performance
with an average success rate of 97.9%, including 99.8% on
the Object suite and 96.6% on the Long suite, demonstrat￾ing strong object-centric reasoning and robustness in long￾horizon manipulation

![Simpler]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\5.png"),
On SimplerEnvWidowX, which
evaluates realtosim generalization under diverse visual
conditions, LaRAVLA attains the highest average success
rate of 68.8%, outperforming NoCoT, Textual CoT, and Visual CoT baselines
Across both benchmarks, LaRAVLA
consistently surpasses textual and visual CoT methods, indicating that latent reasoning provides more effective and
stable guidance for action prediction and generalizes better
than explicit CoT supervision

- Realworld
![real1]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\8.png"),
![real2]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\6.png"),

LaRA-VLA consistently
outperforms ACT and GR00T N1.5 across all four long￾horizon real-world manipulation tasks, achieving the high￾est average success rate. The improvements are especially
pronounced on tasks requiring multi-stage reasoning and
sustained temporal coordination, highlighting enhanced robustness to error accumulation over long horizons

3. Analysis
- Ablation
![ablation]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\10.png"),

Ablation study of different forms of CoT supervision on
SimplerEnv. TextCoT denotes explicit textual chainofthought,
Latent TextCoT denotes latent textual chainofthought, and Latent VisCoT denotes latent visual chainofthought

- Latent Collapse
![latent analysi]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\11.png"),

Latent tokens
associated with different reasoning components form wellseparated and semantically coherent clusters, demonstrating
clear functional specialization rather than degeneration into
uniform or uninformative representations


![inference time]("D:\4\ICML\Website\Latent-Reasoning-VLA\static\images\12.png"),
LaRA-VLA
significantly reduces inference latency, achieving 135 ms
per rollout and outperforming all baselines by a large margin.
Compared to explicit CoT methods, this yields up to a 90%
reduction in inference time, demonstrating the efficiency
benefits of latent reasoning without explicit CoT decoding

latent collapse和latent token的部分并排放置，文字放在图像下面