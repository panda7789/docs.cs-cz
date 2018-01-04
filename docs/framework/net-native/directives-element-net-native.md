---
title: Element &lt;Directives&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ca27422889fd33071a02c3a4b6fea0a6ba7eb0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdirectivesgt-element-net-native"></a>Element &lt;Directives&gt; (.NET Native)
Kořenový element v každém souboru direktivy modulu runtime pro [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **\<Direktivy xmlns = "http://schemas.microsoft.com/netfx/2013/01/metadata" >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`xmlns`|Obor názvů XML. Její hodnota je vždycky **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.|  
  
## <a name="child-elements"></a>Podřízené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi.|  
|[\<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md)|Definuje sestavení, jehož podřízené typy a členy typu vyžadují metadata v době běhu.|  
  
## <a name="remarks"></a>Poznámky  
 Každý soubor direktivy modulu runtime může obsahovat jenom jednu `<Directives>` elementu.  
  
 `<Directives>` Element může obsahovat nula nebo jedna [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) elementu a nula, jednu nebo více [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) elementy.  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
