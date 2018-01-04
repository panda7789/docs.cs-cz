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
ms.openlocfilehash: 0f04afd5d061a44f572d95abfb0173ad6fa2ac27
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Jiné protokolu událostí už zaregistrovaný zdroj s tímto názvem
Pokus o byl proveden pro zápis záznamu do protokolu událostí, kde je zadaný zdroj registrovaná s jinou protokolu událostí.  
  
 Je nutné nastavit <xref:System.Diagnostics.EventLog.Source%2A> vlastnost vaší <xref:System.Diagnostics.EventLog> instance komponenty před příslušné součásti zapíše položku do protokolu. V takovém případě systém kontroluje, zda je zadaný zdroj není zaregistrována v protokolu událostí, ke kterému je součást zápisu a volání <xref:System.Diagnostics.EventLog.CreateEventSource%2A> v případě potřeby.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Odebere přidružení zdroje první pomocí protokolu <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> nebo <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metoda.  
  
2.  Zaregistrujte zdroj se nový protokol.  
  
## <a name="see-also"></a>Viz také  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

