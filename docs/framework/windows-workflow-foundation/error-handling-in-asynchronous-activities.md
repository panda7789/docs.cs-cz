---
title: Zpracování chyb v asynchronních aktivitách
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: c63ce231687b03bdba57edd38c32270eabeff834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182950"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="47fe3-102">Zpracování chyb v asynchronních aktivitách</span><span class="sxs-lookup"><span data-stu-id="47fe3-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="47fe3-103">Poskytování zpracování chyb <xref:System.Activities.AsyncCodeActivity> v zahrnuje směrování chyby prostřednictvím systému zpětného volání aktivity.</span><span class="sxs-lookup"><span data-stu-id="47fe3-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="47fe3-104">Toto téma popisuje, jak získat chybu, která je vyvolána v asynchronní operace zpět k hostiteli, pomocí SendMail ukázky aktivity.</span><span class="sxs-lookup"><span data-stu-id="47fe3-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="47fe3-105">Vrácení chyby vyvoláné v asynchronní aktivitě zpět hostiteli</span><span class="sxs-lookup"><span data-stu-id="47fe3-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="47fe3-106">Směrování chyby v asynchronní operaci zpět k hostiteli v ukázce aktivity SendMail zahrnuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="47fe3-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="47fe3-107">Přidejte vlastnost Exception `SendMailAsyncResult` do třídy.</span><span class="sxs-lookup"><span data-stu-id="47fe3-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="47fe3-108">Zkopírujte vyzývavou chybu do této vlastnosti v obslužné rutině `SendCompleted` události.</span><span class="sxs-lookup"><span data-stu-id="47fe3-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="47fe3-109">Vyvolání výjimky `EndExecute` v obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="47fe3-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="47fe3-110">Výsledný kód je následující.</span><span class="sxs-lookup"><span data-stu-id="47fe3-110">The resulting code is as follows.</span></span>  
  
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
