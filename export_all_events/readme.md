# 📤 Export All Events Workflow

This n8n workflow automates the export of event data from an external API using a scroll-based pagination mechanism. It is designed to retrieve large volumes of event records within a specified time window for a given customer.

## 🔧 Workflow Summary

1. **Trigger**: Manually started using the "Test Workflow" button.
2. **Set Variables**: Initializes required parameters, including:
   - `api_key`
   - `customerid`
   - `startTime`
   - `endTime`
3. **Initial Query**: Sends a `POST` request to the API to fetch the first page of event data.
4. **Set Scroll ID & Hits**: Extracts the scroll ID and event records from the response.
5. **Conditional Check**: Evaluates if any events were returned (`hits.length > 0`).
6. **Continued Query**: If events exist, sends a follow-up request using the scroll ID to fetch additional pages.
7. **Aggregation**: Combines all retrieved event records into a single dataset for downstream processing or export.

## 📌 Notes

- Pagination is handled using the `scroll` API pattern with a 5-minute time window (`scroll: "5m"`).
- Records are sorted by time in ascending order.
- Useful for exporting event logs for compliance, audit, or analysis tasks.

## 🏷️ Tags

`Support`, `Events`, `Export`, `Scroll API`

---

**Status**: Inactive (can be manually triggered for testing and development)
