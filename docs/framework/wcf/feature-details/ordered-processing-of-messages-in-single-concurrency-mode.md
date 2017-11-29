---
title: "Uspořádané zpracování zpráv v režimu jedné souběžnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a1acf4c3edb51500c2ead2e4ba33c6d3cc9c953f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Souběžnosti](../../../../docs/framework/wcf/samples/concurrency.md)
