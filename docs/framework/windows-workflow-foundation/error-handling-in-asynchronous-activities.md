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
# <a name="error-handling-in-asynchronous-activities"></a>Zpracování chyb v asynchronních aktivitách
Poskytování zpracování chyb <xref:System.Activities.AsyncCodeActivity> v zahrnuje směrování chyby prostřednictvím systému zpětného volání aktivity. Toto téma popisuje, jak získat chybu, která je vyvolána v asynchronní operace zpět k hostiteli, pomocí SendMail ukázky aktivity.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Vrácení chyby vyvoláné v asynchronní aktivitě zpět hostiteli  
 Směrování chyby v asynchronní operaci zpět k hostiteli v ukázce aktivity SendMail zahrnuje následující kroky:  
  
- Přidejte vlastnost Exception `SendMailAsyncResult` do třídy.  
  
- Zkopírujte vyzývavou chybu do této vlastnosti v obslužné rutině `SendCompleted` události.  
  
- Vyvolání výjimky `EndExecute` v obslužné rutině události.  
  
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
