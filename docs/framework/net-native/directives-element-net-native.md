---
title: <Directives>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 0c6ebb8954e80f3f6dc6733f0e9d76094477689b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84202387"
---
# <a name="directives-element-net-native"></a>\<Directives>– Element (.NET Native)
Kořenový element v každém souboru direktiv modulu runtime pro .NET Native.  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`xmlns`|Obor názvů XML. Jeho hodnota je vždy `http://schemas.microsoft.com/netfx/2013/01/metadata` .|  
  
## <a name="child-elements"></a>Podřízené prvky  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi.|  
|[\<Library>](library-element-net-native.md)|Definuje sestavení, jehož podřízené typy a členové typu v době běhu vyžadují metadata.|  
  
## <a name="remarks"></a>Poznámky  
 Každý soubor direktiv modulu runtime může obsahovat pouze jeden `<Directives>` element.  
  
 `<Directives>`Element může obsahovat nula nebo jeden [\<Application>](application-element-net-native.md) prvek a nula, jeden nebo více [\<Library>](library-element-net-native.md) prvků.  
  
## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
