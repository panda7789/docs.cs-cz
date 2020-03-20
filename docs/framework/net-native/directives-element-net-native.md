---
title: <Directives>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181046"
---
# <a name="directives-element-net-native"></a>\<Direktivy> element (nativní.NET)
Kořenový prvek v každém souboru direktiv runtime pro nativní rozhraní .NET.  
  
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
|`xmlns`|Obor názvů XML. Jeho hodnota je vždy **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.|  
  
## <a name="child-elements"></a>Podřízené prvky  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy pro celou aplikaci a členy typu, jejichž metadata jsou k dispozici pro reflexi.|  
|[\<>knihovny](library-element-net-native.md)|Definuje sestavení, jehož podřízené typy a členy typu vyžadují metadata za běhu.|  
  
## <a name="remarks"></a>Poznámky  
 Každý soubor direktiv runtime direktivy může obsahovat pouze jeden `<Directives>` prvek.  
  
 Prvek `<Directives>` může obsahovat nula nebo jeden [ \<prvek>aplikace](application-element-net-native.md) a nula, jeden nebo více [ \<prvků Library>.](library-element-net-native.md)  
  
## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
