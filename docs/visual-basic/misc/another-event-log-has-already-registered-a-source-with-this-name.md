---
title: Jiný protokol událostí už zaregistrovaný zdroj s tímto názvem
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: fa4e8a022db1bbc19bff38fd529066b0619add68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646105"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Jiný protokol událostí už zaregistrovaný zdroj s tímto názvem
Pokus o byla vytvořena pro zápis záznamu do protokolu událostí, kde zadaný zdroj je zaregistrován jiný protokol událostí.  
  
 Je nutné nastavit <xref:System.Diagnostics.EventLog.Source%2A> vlastnictví vaší <xref:System.Diagnostics.EventLog> instance komponenty předtím, než vaše komponenta zapíše položku do protokolu. Pokud k tomu dojde, systém kontroluje, zda je zadaný zdroj je zaregistrován v protokolu událostí, ke kterému je součást zápisu a volání <xref:System.Diagnostics.EventLog.CreateEventSource%2A> v případě potřeby.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Odebere přidružení zdroje první pomocí protokolu <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> nebo <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metody.  
  
2.  Zaregistrujte zdroj nový protokol.  
  
## <a name="see-also"></a>Viz také:
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)

