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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7c23dec2f92ed8654d5f0460966dc19af0a8405
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling-in-asynchronous-activities"></a>Zpracování chyb v asynchronní aktivity
Zpracování chyb v poskytování <xref:System.Activities.AsyncCodeActivity> zahrnuje směrování chyba prostřednictvím systému aktivity zpětného volání. Toto téma popisuje postup dojde k chybě, která je vyvolána v asynchronní operaci zpět na hostitele, pomocí ukázkové aktivity SendMail.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Vrácení k chybě dojde v aktivitě asynchronní zpět na hostitele  
 Směrování chybu v asynchronní operaci zpět na hostitele v ukázce aktivity SendMail zahrnuje následující kroky:  
  
-   Přidat vlastnost výjimky k `SendMailAsyncResult` třídy.  
  
-   Zkopírujte chyba výjimce dojde k dané vlastnosti v `SendCompleted` obslužné rutiny události.  
  
-   Throw – výjimka `EndExecute` obslužné rutiny události.  
  
 Výsledný kód je následující.  
  
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
