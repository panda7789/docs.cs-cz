---
title: Zpracování chyb v asynchronních aktivitách
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 7a1db144e4738870d3ff5fe68df11b2fb06ef3d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640952"
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
