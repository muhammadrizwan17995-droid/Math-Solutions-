
# =========================================
# RIZWAN AI - ASK ANY MATH QUESTION
# =========================================

def answer_question(question):
    q = question.lower().strip()

    try:
        # Percentage: 15% of 200
        import re

        match = re.fullmatch(
            r"(-?\d+(?:\.\d+)?)\s*%\s*of\s*(-?\d+(?:\.\d+)?)",
            q
        )

        if match:
            percent = float(match.group(1))
            number = float(match.group(2))
            return percent * number / 100

        # Linear equation: 2x+4=10
        match = re.fullmatch(
            r"\s*(-?\d+(?:\.\d+)?)\s*x\s*([+-])\s*"
            r"(\d+(?:\.\d+)?)\s*=\s*(-?\d+(?:\.\d+)?)\s*",
            q
        )

        if match:
            a = float(match.group(1))
            sign = match.group(2)
            b = float(match.group(3))
            c = float(match.group(4))

            if sign == "-":
                b = -b

            if a == 0:
                return "یہ مساوات حل نہیں ہو سکتی۔"

            return f"x = {(c - b) / a}"

        # Math expression and trigonometry
        return calc(
            q.replace("^", "**")
             .replace(" ", "")
        )

    except Exception as e:
        return (
            "سوال سمجھ نہیں آیا۔ مثالیں:\n"
            "25+30\n"
            "sin90\n"
            "sqrt(144)\n"
            "15% of 200\n"
            "2x+4=10"
        )


print("\n🤖 RIZWAN AI MATH MASTER")
print("اپنا سوال لکھیں۔ بند کرنے کے لیے exit لکھیں۔\n")

while True:
    question = input("آپ کا سوال: ").strip()

    if question.lower() in ("exit", "quit", "band"):
        print("Rizwan AI بند ہو رہا ہے۔ اللہ حافظ!")
        break

    result = answer_question(question)
    print("جواب:", result)
    print("-" * 35)