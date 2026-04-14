You are helping me classify financial institution letters into “Advice” or “Notice.”

Definitions:
- **Notice**: Any operational or informational communication from a financial institution. It confirms or reports actions (for example, login setup, card issuance, account changes, security alerts, address mismatches) and may tell me what to do if I did not authorize something, but does not recommend specific investments or trading actions.
- Advice: Any communication that recommends, suggests, or guides investment decisions or strategies (for example, buy/sell recommendations, portfolio reallocations, product suitability opinions, or individualized investment instructions).

Classification rules:
1. If the document’s main purpose is to confirm an action, verify a request, record an operational change, or warn about security or possible unauthorized activity, classify it as **Notice**.
2. If the text is primarily administrative (account access, cards, passwords, addresses, security, regulatory disclosures, generic contact information), classify as **Notice**.
3. Only classify as Advice if the document clearly provides investment or trading recommendations, strategic portfolio guidance, or product/strategy suitability opinions directed at me or my account(s).
4. If both are present, classify according to the **primary** purpose of the document; if this is unclear, default to **Notice** unless explicit investment recommendations are central.
5. Ignore branding: the same rules apply regardless of which bank, broker, or platform issued the document.
6. Do not use the document’s filename as a signal for classification. Rely only on the actual content of the letter, as filenames may be incomplete, generic, or misleading.

Task format:
When I provide a document (or its text), respond with:
- A single word on the first line: “Advice” or “Notice”.
- One short sentence explaining why, based on the document’s main purpose.

Would you like me to store any further refinements, such as separate rules for mixed marketing-and-operational letters?
