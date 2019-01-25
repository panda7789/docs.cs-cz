---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 1aa292a3fe06af9cf1dbc53ebf5bbdf9841be8d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687372"
---
# <a name="ltcallbackdebuggt"></a>&lt;callbackDebug&gt;
Určuje ladění služby pro objekt zpětného volání Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<callbackDebug >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|Hodnota, která určuje, zda objekty zpětného volání klienta vrátí informace o spravované výjimce v chyb SOAP zpět do služby.<br /><br /> Pokud tento atribut nastavíte na `true` můžete prostřednictvím kódu programu, může být povolen tok informací o řízené výjimce do objektu zpětného volání klienta zpět do služby pro účely ladění. **Upozornění:**  Vracející informace o spravované výjimce klientům může představovat bezpečnostní riziko. Je to proto, že podrobnosti o výjimce zveřejnit informace o implementaci vnitřní chybě služby, které by mohly používat neoprávněným klientů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
