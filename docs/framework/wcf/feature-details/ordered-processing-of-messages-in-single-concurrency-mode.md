---
title: Uspořádané zpracování zpráv v režimu jedné souběžnosti
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: ecabb9a6e838b0137c538d76c554646356ea87f5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991505"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Uspořádané zpracování zpráv v režimu jedné souběžnosti
WCF neposkytuje žádné záruky týkající se pořadí, ve kterém jsou zprávy zpracovávány, pokud se nejedná o relace příslušného podkladového kanálu.  Například služba WCF, která používá MsmqInputChannel, která není kanálem relace, nebude schopna zpracovat zprávy v daném pořadí. V některých případech se může stát, že vývojář bude chtít v pořadí zpracování, ale nechce používat relace. Toto téma popisuje, jak toto chování nakonfigurovat, když je služba spuštěna v režimu jedné souběžnosti.  
  
## <a name="in-order-message-processing"></a>Zpracování zpráv v pořadí  
 Do rozhraní <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute>byl přidán nový atribut s názvem. Když <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> je nastavená hodnota true <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a je nastavená na <xref:System.ServiceModel.ConcurrencyMode.Single> zprávy odesílané službě, budou zpracovány v daném pořadí. Následující fragment kódu ukazuje, jak tyto atributy nastavit.  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je hodnota nastavena na jinou hodnotu <xref:System.InvalidOperationException> , je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také:

- [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Souběžnost](../../../../docs/framework/wcf/samples/concurrency.md)
