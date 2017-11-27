---
title: dataContractSerializer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4044e81b7c33c7a755678e79586dd4f37cf54ed5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datacontractserializer"></a>dataContractSerializer
Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<dataContractSerializer >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|ignoreExtensionDataObject|Logická hodnota, která určuje, jestli se ignorovat data poskytl koncového bodu, když je právě serializován nebo deserializován.|  
|maxItemsInObjectGraph|Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Najdete v článku <xref:System.Runtime.Serialization.DataContractSerializer> dokumentace pro další informace o známé typy.  
  
> [!CAUTION]
>  `<dataContractSerializer>` Element chování (pokud existuje) vždy zobrazit před `<enableWebScript>` chování element v konfiguračním souboru. Jinak jejich výsledné chování není definován.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [Známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Přenos a serializace dat](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
