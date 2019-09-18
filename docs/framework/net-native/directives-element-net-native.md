---
title: <Directives>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ec9a09e2fc03adbfcff0d7e69489e37da6e4a5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049882"
---
# <a name="directives-element-net-native"></a>\<Direktivy > element (.NET Native)
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
|`xmlns`|Obor názvů XML. Jeho hodnota je vždy **"http://schemas.microsoft.com/netfx/2013/01/metadata"** .|  
  
## <a name="child-elements"></a>Podřízené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi.|  
|[\<Library>](library-element-net-native.md)|Definuje sestavení, jehož podřízené typy a členové typu v době běhu vyžadují metadata.|  
  
## <a name="remarks"></a>Poznámky  
 Každý soubor direktiv modulu runtime může obsahovat pouze `<Directives>` jeden element.  
  
 Element může obsahovat nula nebo jeden [ \<> element aplikace](application-element-net-native.md) a žádnou, jednu nebo více [ \<> prvků knihovny.](library-element-net-native.md) `<Directives>`  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
