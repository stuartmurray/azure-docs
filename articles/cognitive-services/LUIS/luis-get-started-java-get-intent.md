---
title: Call a Language Understanding (LUIS) app using Java | Microsoft Docs 
description: Learn to call a LUIS app using Java. 
services: cognitive-services
author: DeniseMak
manager: rstand

ms.service: cognitive-services
ms.technology: luis
ms.topic: article
ms.date: 12/13/2017
ms.author: v-demak
---

# Call a LUIS app using Java
Pass utterances to a LUIS endpoint and get intent and entities back.

## Before you begin
You need a Cognitive Services API key to make calls to the sample LUIS app we use in this walkthrough. 
To get an API key follow these steps: 
  1. You first need to create a [Cognitive Services API account](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-apis-create-account) in the Azure portal. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) before you begin.
  2. Log in to the Azure portal at https://portal.azure.com. 
  3. Follow the steps in [Creating Subscription Keys using Azure](./AzureIbizaSubscription.md) to get a key.
  4. Go back to the [LUIS](luis-reference-regions.md) website and log in using your Azure account. 

## Understand what LUIS returns

To understand what a LUIS app returns, you can paste the URL of a sample LUIS app into a browser window. The sample app you'll use is an IoT app that detects whether the user wants to turn on or turn off lights.

1. The endpoint of the sample app is in this format: `https://westus.api.cognitive.microsoft.com/luis/v2.0/apps/df67dcdb-c37d-46af-88e1-8b97951ca1c2?subscription-key=<YOUR_API_KEY>&verbose=false&q=turn%20on%20the%20bedroom%20light` Copy the URL and substitute your subscription key for the value of the `subscription-key` field.
2. Paste the URL into a browser window and press Enter. The browser displays a JSON result that indicates that LUIS detects the `HomeAutomation.TurnOn` intent and the `HomeAutomation.Room` entity with the value `bedroom`.

    ![JSON result detects the intent TurnOn](./media/luis-get-started-java-get-intent/turn-on-bedroom.png)
3. Change the value of the `q=` parameter in the URL to `turn off the living room light`, and press enter. The result now indicates that the LUIS detected the `HomeAutomation.TurnOff` intent and the `HomeAutomation.Room` entity with value `living room`. 

    ![JSON result detects the intent TurnOff](./media/luis-get-started-java-get-intent/turn-off-living-room.png)


## Consume a LUIS result using the Endpoint API with Java 

You can use Java to access the same results you saw in the browser window in the previous step. 
1. Copy the following code to create a class in your IDE:

   [!code-java[Console app code that calls a LUIS endpoint](~/samples-luis/documentation-samples/endpoint-api-samples/java/call-endpoint.java)]
2. Replace the value of the `SubscriptionKey` variable with your LUIS subscription key.

3. In your IDE, add references to `httpclient` and `httpcore` libraries.

4. Run the console application. It displays the same JSON that you saw earlier in the browser window.

![Console window displays JSON result from LUIS](./media/luis-get-started-java-get-intent/console-turn-on.png)

## Next steps
> [!div class="nextstepaction"]
> [Add utterances](luis-quickstart-java-add-utterance.md)
