---
title: "Zpracování chyb v asynchronní aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7606aeeeb3e2e583f9a217b78bcae4aebc6d8662
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="95311-102">Zpracování chyb v asynchronní aktivity</span><span class="sxs-lookup"><span data-stu-id="95311-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="95311-103">Zpracování chyb v poskytování <xref:System.Activities.AsyncCodeActivity> zahrnuje směrování chyba prostřednictvím systému aktivity zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="95311-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="95311-104">Toto téma popisuje postup dojde k chybě, která je vyvolána v asynchronní operaci zpět na hostitele, pomocí ukázkové aktivity SendMail.</span><span class="sxs-lookup"><span data-stu-id="95311-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="95311-105">Vrácení k chybě dojde v aktivitě asynchronní zpět na hostitele</span><span class="sxs-lookup"><span data-stu-id="95311-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="95311-106">Směrování chybu v asynchronní operaci zpět na hostitele v ukázce aktivity SendMail zahrnuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="95311-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
-   <span data-ttu-id="95311-107">Přidat vlastnost výjimky k `SendMailAsyncResult` třídy.</span><span class="sxs-lookup"><span data-stu-id="95311-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
-   <span data-ttu-id="95311-108">Zkopírujte chyba výjimce dojde k dané vlastnosti v `SendCompleted` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="95311-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
-   <span data-ttu-id="95311-109">Throw – výjimka `EndExecute` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="95311-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="95311-110">Výsledný kód je následující.</span><span class="sxs-lookup"><span data-stu-id="95311-110">The resulting code is as follows.</span></span>  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }   
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;   
        }  
    }  
```
