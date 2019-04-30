---
title: Zpracování chyb v asynchronních aktivitách
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 4a7cbecef596eec6eaa128b8ffc7bc5c6e4b79bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773994"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="e50f4-102">Zpracování chyb v asynchronních aktivitách</span><span class="sxs-lookup"><span data-stu-id="e50f4-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="e50f4-103">Poskytuje zpracování chyb v <xref:System.Activities.AsyncCodeActivity> zahrnuje směrování chyby pomocí zpětného volání systému aktivity.</span><span class="sxs-lookup"><span data-stu-id="e50f4-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="e50f4-104">Toto téma popisuje, jak dojde k chybě, která je vyvolána v asynchronní operaci zpět na hostitele, pomocí ukázková aktivita SendMail.</span><span class="sxs-lookup"><span data-stu-id="e50f4-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="e50f4-105">Vrátit chybu vyvolána v aktivitě asynchronní zpět k hostiteli</span><span class="sxs-lookup"><span data-stu-id="e50f4-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="e50f4-106">Směrování chybu v asynchronní operaci zpět na hostitele v ukázce aktivita SendMail zahrnuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="e50f4-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="e50f4-107">Přidejte vlastnosti Exception k `SendMailAsyncResult` třídy.</span><span class="sxs-lookup"><span data-stu-id="e50f4-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="e50f4-108">K této výjimce dojde Chyba kopírování na tuto vlastnost v `SendCompleted` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e50f4-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="e50f4-109">Vyvolání výjimky `EndExecute` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e50f4-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="e50f4-110">Výsledný kód je následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e50f4-110">The resulting code is as follows.</span></span>  
  
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
