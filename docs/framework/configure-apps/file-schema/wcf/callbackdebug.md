---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 2103c32112b6c5554d7b510f486d4cbb1349f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747944"
---
# <a name="ltcallbackdebuggt"></a>&lt;callbackDebug&gt;
Určuje, služba ladění pro objekt zpětného volání Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<callbackDebug >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|Hodnota, která určuje, zda objekty zpětné volání klienta vrátit informace o spravovaných výjimce v chyb SOAP zpět ke službě.<br /><br /> Pokud tento atribut nastavíte na `true` prostřednictvím kódu programu, můžete povolit tok spravovaných výjimek informací v objektu zpětné volání klienta zpět na službu pro účely ladění. **Upozornění:** vrácení informací o spravovaných výjimce klientům může být bezpečnostní riziko. To je proto podrobnosti o výjimce zveřejnění informace o interní služby implementace, která může neoprávněným klienty.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
