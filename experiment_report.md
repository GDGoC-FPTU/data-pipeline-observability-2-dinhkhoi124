# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600615  
**Name:** DINH VAN ANH KHOI  
**Date:** 10/06/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario                          | Agent Response                                                          | Accuracy (1-10) | Notes                                                                                                                     |
| --------------------------------- | ----------------------------------------------------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200.            | 9               | Du lieu da duoc validate va transform. Ket qua hop ly vi Laptop la san pham electronics co gia cao nhat trong clean data. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2               | Du lieu co outlier va loi chat luong nen agent dua ra ket qua khong phu hop voi ngu canh san pham thong thuong.           |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai khi dung `garbage_data.csv` vi bo du lieu nay co nhieu van de ve chat luong. File co duplicate ID, vi Laptop va Banana cung co `id = 1`. Ngoai ra, record Broken Chair co `price` la chuoi `ten dollars` thay vi so, lam du lieu khong dong nhat ve kieu du lieu. Record Nuclear Reactor co gia `999999`, day la mot outlier rat lon trong category electronics. Record Ghost Item lai thieu `id`, co gia bang 0 va category rong. Agent simulation chi loc category electronics va chon san pham co gia cao nhat, nen no bi outlier Nuclear Reactor anh huong truc tiep va dua ra cau tra loi sai/khong hop ly.

Khi dung `processed_data.csv`, cac record loi da bi loai bo, category duoc chuan hoa va price la du lieu hop le. Vi vay agent co knowledge base sach hon va cau tra loi dang tin cay hon. Thi nghiem nay cho thay neu du lieu dau vao kem chat luong, agent co the van chay khong loi nhung ket qua bi sai lech.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Mot prompt tot khong the sua het loi neu du lieu nen tang bi sai, thieu hoac co outlier qua lon. Trong thi nghiem nay, cung mot cau hoi nhung clean data cho ket qua hop ly, con garbage data lam agent chon Nuclear Reactor. Vi vay, viec validate, transform va quan sat chat luong du lieu la buoc quan trong truoc khi dua du lieu vao AI agent.
