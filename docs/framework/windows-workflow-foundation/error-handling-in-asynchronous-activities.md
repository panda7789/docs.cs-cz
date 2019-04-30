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
# <a name="error-handling-in-asynchronous-activities"></a>Zpracování chyb v asynchronních aktivitách
Poskytuje zpracování chyb v <xref:System.Activities.AsyncCodeActivity> zahrnuje směrování chyby pomocí zpětného volání systému aktivity. Toto téma popisuje, jak dojde k chybě, která je vyvolána v asynchronní operaci zpět na hostitele, pomocí ukázková aktivita SendMail.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Vrátit chybu vyvolána v aktivitě asynchronní zpět k hostiteli  
 Směrování chybu v asynchronní operaci zpět na hostitele v ukázce aktivita SendMail zahrnuje následující kroky:  
  
- Přidejte vlastnosti Exception k `SendMailAsyncResult` třídy.  
  
- K této výjimce dojde Chyba kopírování na tuto vlastnost v `SendCompleted` obslužné rutiny události.  
  
- Vyvolání výjimky `EndExecute` obslužné rutiny události.  
  
 Výsledný kód je následujícím způsobem.  
  
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
