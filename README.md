# WFDB
1.	步骤1：运行 dataset-1.py，把 CWRU 原始 .mat 驱动端信号处理成 RGB 图像样本，同时生成 signal_image_map.pkl。
2.	步骤2：运行 dataset-filter.py 与类别均衡脚本，完成样本筛选与故障类过采样/Normal 类下采样。
3.	步骤3：如果做创新点1，使用 prepare_manifest_fault4_iid_split.py 或 make_manifest_crossload.py / make_manifest_fewshot.py 生成 2D manifest，然后用 train_innov1_ablation_2d.py 或 run_innov1_suite_iid.py 训练；最后用 summarize_innov1_results.py 汇总。
4.	步骤4：如果做创新点2，先运行 3D 样本构建脚本，把连续 RGB 图像堆叠成 npz clip；然后用 data/make_manifest_crossload_by_load.py 生成 3D manifest。
5.	步骤5：使用 train_innov2_ablation_3d.py 或 run_innov2_suite_crossload.py 训练 3D 模型；若做四折 clean，直接用 scripts/run_crossload_4fold.py。
6.	步骤6：使用 evaluate_test_by_load_and_perturb.py 或 scripts/batch_eval_by_load_and_noise.py 做 clean / scale / mask / gaussian 评估；最后用 summarize_clean_4fold_results.py 和 scripts/summarize_eval_results.py 生成论文总表。
