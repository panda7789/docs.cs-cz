---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 91e7bd63bf496f2c38776d88173ed2ac12a3b888
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926306"
---
# <a name="callbackdebug"></a>\<callbackDebug >
Určuje ladění služby pro objekt zpětného volání služby Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<> chování  
\<endpointBehaviors>  
\<> chování  
\<callbackDebug >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a>type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|Hodnota, která určuje, zda objekty zpětného volání klienta vracejí informace o spravované výjimce v chybách protokolu SOAP zpět do služby.<br /><br /> Pokud tento atribut nastavíte na `true` programové, můžete povolit tok informací o spravovaných výjimkách v objektu zpětného volání klienta zpátky do služby pro účely ladění. **Upozornění**  Vrácení informací o spravované výjimce klientům může představovat bezpečnostní riziko. Důvodem je skutečnost, že podrobnosti o výjimce zpřístupňují informace o implementaci interní služby, které by mohly být používány neautorizovanými klienty.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
