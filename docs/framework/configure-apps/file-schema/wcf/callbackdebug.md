---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccb48efcdd1924ade27220a685e146a7f5eeef76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcallbackdebuggt"></a>&lt;callbackDebug&gt;
Určuje služby ladění pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] objekt zpětného volání.  
  
 \<systém. ServiceModel >  
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
