---
title: Sledování proměnných a argumentů
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: c5d3fe6626c22184edd83de6aedad8589ab2ef35
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837542"
---
# <a name="variable-and-argument-tracking"></a>Sledování proměnných a argumentů
Při sledování provádění pracovního postupu je často užitečné extrahovat data. To poskytuje další kontext při přístupu ke sledování záznamu po provedení. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]můžete extrahovat všechny viditelné proměnné nebo argumenty v rámci rozsahu jakékoli aktivity pracovního postupu pomocí sledování. Sledování profilů usnadňuje extrahování dat.  
  
## <a name="variables-and-arguments"></a>Proměnné a argumenty  
 Proměnné a argumenty jsou extrahovány, když aktivita vygeneruje ActivityStateRecord.  Proměnná je k dispozici pro extrakci pouze v případě, že je v rámci rozsahu aktivity. Proměnná, která se má extrahovat v rámci aktivity, je specifikována následujícím způsobem:  
  
- Pokud je proměnná určena názvem proměnné, pak sledování vyhledá proměnnou v rámci aktuální aktivity, která je sledována a v nadřazených aktivitách. Proměnná je prohledávána v oboru aktuální aktivity a v nadřazeném oboru.  
  
- Pokud proměnné, které mají být extrahovány, jsou určeny pomocí názvu = "\*", pak jsou extrahovány všechny proměnné v rámci aktuální aktivity, které jsou sledovány. V tomto případě proměnné, které jsou v oboru, ale nejsou definovány v nadřazených aktivitách, nejsou extrahovány.  
  
 Při extrakci argumentů závisí argumenty, které jsou extrahovány, na stav aktivity. Když je spuštěn stav aktivity, jsou k extrakci k dispozici pouze `InArguments`. Pro extrakci jsou k dispozici všechny argumenty pro všechny ostatní stavy aktivity (uzavřeno, chyba, zrušeno).  
  
 Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování záznamu sledování `Closed` aktivity. Proměnné a argumenty lze extrahovat pouze pomocí <xref:System.Activities.Tracking.ActivityStateRecord> a proto se přihlásí k odběru v rámci profilu sledování pomocí <xref:System.Activities.Tracking.ActivityStateQuery>.  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Ochrana informací uložených v proměnných a argumentech  
 Sledovaná proměnná nebo argument je ve výchozím nastavení viditelná modulem runtime WF. Vývojář pracovního postupu může chránit před tím, že provádí následující kroky:  
  
1. Zašifrujte hodnotu proměnné.  
  
2. Řízení vytváření profilu sledování, aby se zabránilo extrakci proměnné nebo argumentu.  
  
3. Pro vlastní účastníky sledování zajišťuje, že kód WF nezveřejňuje citlivé informace, které jsou uloženy v proměnných nebo argumentech.  
  
## <a name="see-also"></a>Viz také:

- [Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
