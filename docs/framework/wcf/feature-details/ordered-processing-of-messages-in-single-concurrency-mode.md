---
title: Uspořádané zpracování zpráv v režimu jedné souběžnosti
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: c9f2460a1def19212d3ba866b0b443830e9b69bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745844"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Uspořádané zpracování zpráv v režimu jedné souběžnosti
WCF neposkytuje žádnou záruku o pořadí, ve kterém se zprávy zpracovávají, pokud je základní kanál s relacemi.  Například službu WCF používající MsmqInputChannel, který není kanál s relacemi, nepůjde zpracovat zprávy v pořadí. Existují některé okolnosti, kdy může vývojář má v pořadí zpracování chování ale nebudete chtít použít relace. Toto téma popisuje, jak konfigurovat toto chování, pokud služba běží v režimu jedné souběžnosti.  
  
## <a name="in-order-message-processing"></a>Zpracování zpráv v pořadí  
 Volá se nový atribut <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> byl přidán do <xref:System.ServiceModel.ServiceBehaviorAttribute>. Když <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> je nastavena na hodnotu true a <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastavena na <xref:System.ServiceModel.ConcurrencyMode.Single> zprávy odeslané do služby se zpracovávají v pořadí. Následující fragment kódu ukazuje, jak nastavit tyto atributy.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastavena na jakoukoli jinou hodnotu <xref:System.InvalidOperationException> je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také:
- [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Souběžnost](../../../../docs/framework/wcf/samples/concurrency.md)
