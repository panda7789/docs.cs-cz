---
title: "Jiné protokolu událostí už zaregistrovaný zdroj s tímto názvem"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8beea344d233794ddc36d7fc53db1c01be84399f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Jiné protokolu událostí už zaregistrovaný zdroj s tímto názvem
Pokus o byl proveden pro zápis záznamu do protokolu událostí, kde je zadaný zdroj registrovaná s jinou protokolu událostí.  
  
 Je nutné nastavit <xref:System.Diagnostics.EventLog.Source%2A> vlastnost vaší <xref:System.Diagnostics.EventLog> instance komponenty před příslušné součásti zapíše položku do protokolu. V takovém případě systém kontroluje, zda je zadaný zdroj není zaregistrována v protokolu událostí, ke kterému je součást zápisu a volání <xref:System.Diagnostics.EventLog.CreateEventSource%2A> v případě potřeby.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Odebere přidružení zdroje první pomocí protokolu <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> nebo <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metoda.  
  
2.  Zaregistrujte zdroj se nový protokol.  
  
## <a name="see-also"></a>Viz také  
 [My.Application.Log – objekt](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [Postupy: odebrání zdroje událostí](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)  
 [Postupy: Přidání aplikace jako zdroj položek protokolu událostí](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
