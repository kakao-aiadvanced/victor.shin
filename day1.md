# 다운로드한 가장큰 모델
mixtral:8x7b


# Formatted Prompt Generation 

## 프롬프트

### 직접 작성한 프롬프트
We need a customer support triage system for a game. Requests can be categorized as Payment, Game Bug, or Game Improvement. If the issue is related to Payment, an engineer can be notice by sms.

Please write a prompt that reviews an incoming message and determines the appropriate category, along with a brief explanation for that decision.

<customer_message>
{{CUSTOMER_MESSAGE}}
</customer_message>


### Claude가 만들어준 프롬프트

You are a customer support triage system for a mobile game. Your task is to categorize incoming customer messages into one of three categories: Payment, Game Bug, or Game Improvement. You will also provide a brief explanation for your categorization decision.

Here is the customer message you need to categorize:

<customer_message>
{{CUSTOMER_MESSAGE}}
</customer_message>

Please carefully read and analyze the content of the message. Then, categorize it into one of the following categories:

1. Payment: Issues related to transactions, billing, purchases, or any financial aspects of the game.
2. Game Bug: Technical issues, glitches, or unexpected behavior within the game.
3. Game Improvement: Suggestions, feature requests, or feedback about game mechanics, design, or content.

After determining the appropriate category, provide a brief explanation for your decision. Consider the main focus of the customer's message and which category best addresses their concern.

Present your decision and explanation in the following format:

<category_decision>
Category: [Your chosen category]
Explanation: [Your brief explanation for choosing this category]
</category_decision>

If the category you've chosen is "Payment", please include the following note after your category decision:

<engineer_notification>
Note: An engineer should be notified by SMS about this payment-related issue.
</engineer_notification>

Remember to base your decision solely on the content of the customer's message. Do not make assumptions beyond what is explicitly stated or strongly implied in the message.


## 예시

### 직접 작성한 예시
login error occured. Please help me


### Claude가 작성한 예시
Hey there! I just bought 1000 gems in the game, but they're not showing up in my account. I've already been charged $9.99 on my credit card. Can you please help me get my gems or refund the money? This is really frustrating!


## 프롬프트 실행결과


### user가 작성한 프롬프트를 실행했을 때의 답변 확인 및 평가, 결과 비교
#### message (by user)
I buy $10000000 items. But I can't see it in the game

#### model output
# Customer Support Triage Prompt

Review the customer message below and categorize it as:
- **Payment**: Issues related to purchases, billing, transactions, missing purchased items
- **Game Bug**: Technical problems, crashes, glitches, or unexpected behavior in the game
- **Game Improvement**: Suggestions, feature requests, or feedback to enhance the game

Then provide a brief explanation for your categorization decision.

---

**Customer Message:**
```
I buy $10000000 items. But I can't see it in the game
```

**Category: Payment**

**Explanation:** This is a payment-related issue because the customer has purchased in-game items ($10000000 worth) but is reporting that the purchased items are not appearing in their game. This involves a transaction problem where the customer paid for something they haven't received, making it a payment issue that requires attention from the payment systems team.

**Action Required:** Notify engineer via SMS due to payment-related nature of this issue.


### Claude가 작성한 프롬프트를 실행했을 때의 답변 확인 및 평가, 결과 비교
#### message (by user)
I buy $10000000 items. But I can't see it in the game

#### model output
<category_decision>
Category: Payment
Explanation: The customer's message is about purchasing items worth $10000000 but not being able to see these purchased items in the game. This is primarily a payment issue because it involves a transaction that was completed but the purchased items are not visible in the game. This is a direct problem with a financial transaction and its expected outcome.
</category_decision>

<engineer_notification>
Note: An engineer should be notified by SMS about this payment-related issue.
</engineer_notification>

#### message (by claude)
Hey there! I've been playing your game for a while now and I absolutely love it. However, I've noticed that the new character I unlocked last week, the Fire Mage, seems to be causing my game to crash whenever I use their ultimate ability. It's really frustrating because I spent a lot of time trying to unlock this character. Is this a known issue? Can you please fix it soon? I'd love to be able to use my new character without worrying about the game crashing. Thanks for your help!

#### model output
I'll analyze this customer message and categorize it appropriately.

<category_decision>
Category: Game Bug
Explanation: The customer is reporting that their game crashes whenever they use the Fire Mage character's ultimate ability. This is clearly a technical issue/glitch that's preventing normal gameplay functionality, which falls under the Game Bug category. The customer is not reporting a payment issue or suggesting an improvement to the game - they're describing unexpected behavior (crashing) that needs to be fixed.
</category_decision>
