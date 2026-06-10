[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112804&assignment_repo_type=AssignmentRepo)

# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** dinhkhoi1work@gmail.com  
**Name:** Dinh Van Anh Khoi

---

## Mo ta

Day 10 Lab nay xay dung mot ETL pipeline don gian bang Python de doc du lieu san pham tu file JSON, kiem tra chat luong du lieu, chuan hoa du lieu va xuat ket qua ra CSV.

Nhung phan da hoan thanh trong `solution.py`:

- **Extract:** doc du lieu tu `raw_data.json` bang `json.load()`.
- **Validate:** loai bo record co `price <= 0` hoac `category` bi rong.
- **Transform:** tinh `discounted_price = price * 0.9`, chuan hoa `category` sang Title Case va them cot `processed_at`.
- **Load:** luu DataFrame da xu ly vao `processed_data.csv`.
- **Observability:** in log so record duoc giu lai, so record bi loai va ly do bi loai.

---

## Cach chay

### Prerequisites

```bash
pip install pandas
```

### Chay ETL Pipeline

```bash
python solution.py
```

Ket qua mong doi:

```text
==================================================
ETL Pipeline Started...
==================================================
Extracting data from raw_data.json...
Validation summary: 3 kept, 2 dropped.
Errors found: [{'id': 3, 'reason': 'Price <= 0'}, {'id': 4, 'reason': 'Missing Category'}]
Successfully loaded 3 records to processed_data.csv

Pipeline completed! 3 records saved.
```

### Chay Agent Simulation

```bash
python agent_simulation.py
```

Thi nghiem nay so sanh ket qua agent khi dung du lieu sach trong `processed_data.csv` va du lieu ban trong `garbage_data.csv`.

Ket qua hien tai:

```text
Testing with CLEAN data:
Agent: Based on my data, the best choice is Laptop at $1200.

Testing with GARBAGE data:
Agent: Based on my data, the best choice is Nuclear Reactor at $999999.
```

---

## Cau truc thu muc

```text
.
|-- solution.py              # ETL pipeline script
|-- raw_data.json            # Du lieu dau vao
|-- processed_data.csv       # Output sau khi ETL
|-- garbage_data.csv         # Du lieu ban dung de stress test agent
|-- agent_simulation.py      # Agent simulation clean vs garbage data
|-- experiment_report.md     # Bao cao thi nghiem
|-- tests/                   # Autograder tests
`-- README.md                # File huong dan nay
```

---

## Ket qua

Du lieu ban dau trong `raw_data.json` co 5 records. Pipeline da xu ly:

- **3 records hop le:** Laptop, Chair, Monitor.
- **2 records bi loai:** Mystery Box vi `price <= 0`, Phone vi `category` rong.
- File output `processed_data.csv` co them cot `discounted_price` va `processed_at`.

Ket qua cho thay chat luong du lieu anh huong truc tiep den cau tra loi cua agent. Khi dung clean data, agent chon san pham hop ly la Laptop. Khi dung garbage data, agent bi anh huong boi outlier va chon Nuclear Reactor voi gia bat thuong `$999999`.
