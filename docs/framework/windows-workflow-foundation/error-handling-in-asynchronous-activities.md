---
title: Zpracování chyb v asynchronní aktivity
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 4a7cbecef596eec6eaa128b8ffc7bc5c6e4b79bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511979"
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
