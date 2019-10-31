---
title: <Directives> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: abe2e7221e0afb984a6178b12fabc36ea24deb35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128474"
---
# <a name="directives-element-net-native"></a>\<direktivy > elementu (.NET Native)
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
|[\<> aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi.|  
|[> knihovny \<](library-element-net-native.md)|Definuje sestavení, jehož podřízené typy a členové typu v době běhu vyžadují metadata.|  
  
## <a name="remarks"></a>Poznámky  
 Každý soubor direktiv modulu runtime může obsahovat pouze jeden `<Directives>` element.  
  
 Element `<Directives>` může obsahovat nula nebo jeden [\<> prvek aplikace](application-element-net-native.md) a nula, jeden nebo více [knihoven\<](library-element-net-native.md) prvků.  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
