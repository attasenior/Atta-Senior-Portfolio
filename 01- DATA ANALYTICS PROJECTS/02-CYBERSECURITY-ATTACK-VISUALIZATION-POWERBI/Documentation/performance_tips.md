# 🚀 Performance Tips

Optimizing Power BI for large-scale cybersecurity data.

---

## 🧹 Power Query Best Practices

- Remove unused columns early
- Normalize text fields (capitalize, trim, clean)
- Derive calculated columns in Power Query when possible
- Use conditional columns for severity logic

---

## 📊 Data Model Optimization

- Disable Auto Date/Time (File → Options → Data Load)
- Use a dedicated Date table for time intelligence
- Apply star schema: fact table + dimension tables
- Avoid bi-directional relationships unless necessary

---

## 📈 Visual Performance

- Use Top N filters in visuals (not in queries)
- Avoid high-cardinality slicers (e.g., full IP lists)
- Use aggregated measures instead of raw columns
- Prefer Import mode unless real-time data is required

---

## 🧠 DAX Efficiency

- Use `VAR` to store intermediate results
- Use `DIVIDE()` instead of `/` to avoid errors
- Avoid complex logic inside visuals — precompute in measures

---

## 🧭 UX & Navigation

- Use bookmarks for page transitions
- Use drillthrough for detailed views
- Disable unnecessary visual interactions

---

These tips ensure smooth performance, fast rendering, and scalable analytics across your dashboards.
