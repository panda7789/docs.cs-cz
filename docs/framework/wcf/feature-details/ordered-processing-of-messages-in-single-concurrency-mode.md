---
title: Uspořádané zpracování zpráv v režimu jedné souběžnosti
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: bbbc1f62931abda438c3d06b514518b1199b649e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Uspořádané zpracování zpráv v režimu jedné souběžnosti
WCF umožňuje žádné záruky o pořadí, ve kterém jsou zpracovány zprávy, není-li základní kanál relacemi.  Pro instanci služby WCF, který používá MsmqInputChannel, která není kanál s relacemi, se nezdaří zpracování zpráv v pořadí. Existují některé okolnosti, kdy může vývojář má v pořadí zpracování chování ale použít relací. Toto téma popisuje postupy pro konfiguraci tohoto chování, když služba běží v režimu jedné souběžnosti.  
  
## <a name="in-order-message-processing"></a>Pořadí zpracování zpráv  
 Volá se nový atribut <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> byl přidán do <xref:System.ServiceModel.ServiceBehaviorAttribute>. Když <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> je nastaven na hodnotu true a <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastaven na <xref:System.ServiceModel.ConcurrencyMode.Single> zprávy odeslané do služby budou zpracovány v pořadí. Následující fragment kódu ukazuje, jak nastavit tyto atributy.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> nastavena na žádné jiné hodnoty, <xref:System.InvalidOperationException> je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Souběžnost](../../../../docs/framework/wcf/samples/concurrency.md)
