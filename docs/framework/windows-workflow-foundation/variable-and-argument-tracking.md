---
title: "Proměnné a Argument sledování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50bcb67fa4f51318ef7afa69e37d03bb80400539
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="variable-and-argument-tracking"></a>Proměnné a Argument sledování
Při spuštění pracovního postupu pro sledování, je často užitečné extrahovat data. To poskytuje další kontext při přístupu k provádění sledování záznamů post. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], můžete rozbalit žádné viditelné proměnné nebo argumentu v rámci oboru všechny aktivity v pracovním postupu pomocí sledování. Sledování profily usnadňují extrahovat data.  
  
## <a name="variables-and-arguments"></a>Proměnné a argumenty  
 Proměnné a argumenty se extrahují, když aktivita vysílá ActivityStateRecord.  Proměnné je k dispozici pro extrakci, pouze pokud je v rámci oboru aktivity. Proměnné v aktivitě extrahovat je určena následujícím způsobem:  
  
-   Pokud je proměnná Určuje název proměnné, sledování vypadá pro proměnné v rámci aktuální aktivita sledovaných a v nadřazené aktivity. V aktuálním oboru aktivity a v nadřazeném oboru, prohledají se proměnná.  
  
-   Pokud jsou zadané proměnné k extrakci pomocí názvu = "*", pak všechny proměnné v rámci aktuální aktivita sledovaných extrahují. V takovém případě proměnné, jsou v oboru ale definovaný v nadřazené aktivity nejsou extrahovány.  
  
 Při extrahování argumenty, argumenty extrahovat závisí na stavu aktivity. Pokud stav aktivity je zpracování, pak pouze `InArguments` jsou k dispozici pro extrakci. Pro všechny ostatní aktivity stavu (uzavřeno, Faulted zrušená.) všechny argumenty, InArguments a OutArguments, jsou k dispozici pro extrakci.  
  
 Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované. Proměnné a argumenty lze extrahovat jenom s <xref:System.Activities.Tracking.ActivityStateRecord> a proto předplacené v rámci sledování profilu pomocí <xref:System.Activities.Tracking.ActivityStateQuery>.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Ochrana informace uložené v proměnné a argumenty  
 Sledované proměnné nebo argument je ve výchozím nastavení dostupná modulem runtime pracovního postupu. Vývojář pracovního postupu chrání před přístupem provedením následujících kroků:  
  
1.  Hodnotu proměnné zašifrujte.  
  
2.  Ovládací prvek vytváření profilu sledování zabránit extrahování proměnné nebo argumentu.  
  
3.  Pro vlastní sledování účastníky ujistěte, že kód WF nesmí vyzradit citlivé informace, které je uložené v proměnné nebo argumenty.  
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
