---
title: Sledování proměnných a argumentů
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: ef2d6111d5c123ac6c684df09f03398340a5522c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231031"
---
# <a name="variable-and-argument-tracking"></a>Sledování proměnných a argumentů
Při sledování provádění pracovního postupu, je často užitečné extrahovat data. Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], můžete extrahovat všechny viditelné proměnné nebo argumentu v rámci oboru žádnou aktivitu v pracovním postupu pomocí sledování. Sledování profily umožňují snadno extrahovat data.  
  
## <a name="variables-and-arguments"></a>Proměnné a argumenty  
 Pokud aktivita vyzařuje ActivityStateRecord se extrahují proměnné a argumenty.  Proměnná je k dispozici pro extrahování, pouze pokud je v rámci oboru aktivity. Tímto způsobem je zadána proměnná extrahovaným v rámci aktivity:  
  
-   Pokud proměnná je určen název proměnné, sledování vypadá pro proměnné v rámci aktuální aktivitu sledován a v nadřazené aktivity. Proměnná vyhledává v aktuálním oboru aktivity a v nadřazeném oboru.  
  
-   Pokud proměnné extrahovaným je určené vlastností name = "*", pak se extrahují všechny proměnné v rámci aktuální aktivitu sledován. V tomto případě proměnné, které jsou v oboru, ale definované v nadřazeném prvku, které nejsou extrahována aktivity.  
  
 Při extrahování argumenty, argumenty extrahovat závisí na stavu aktivity. Když stav aktivity je zpracování, pak pouze `InArguments` jsou k dispozici pro extrakci. Pro všechny ostatní aktivity stavu (uzavřeno, Faulted, zrušeno) všechny argumenty, InArguments a OutArguments, jsou k dispozici pro extrakci.  
  
 Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován. Proměnné a argumenty může být extrahována pouze pomocí <xref:System.Activities.Tracking.ActivityStateRecord> a tedy přihlášení k odběru v rámci sledovacích profilu pomocí <xref:System.Activities.Tracking.ActivityStateQuery>.  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Ochrana informací uložených v proměnné a argumenty  
 Sledované proměnné nebo argumentu je ve výchozím nastavení nastavena jako viditelná modulem runtime pracovního postupu. Pracovní postup vývojář chránil přístup podle následujících kroků:  
  
1.  Šifrování hodnotu proměnné.  
  
2.  Ovládací prvek pro vytváření profilu sledování, aby se zabránilo extrakce proměnné nebo argumentu.  
  
3.  Pro vlastní sledování účastníci Ujistěte se, že kód WF nesmí vyzradit citlivé informace, které je uložený v proměnných nebo argumentů.  
  
## <a name="see-also"></a>Viz také:

- [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
