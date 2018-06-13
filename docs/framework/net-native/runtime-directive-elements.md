---
title: Elementy direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b4e8f0902e0d3ebd010ff639b329707881c29fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398011"
---
# <a name="runtime-directive-elements"></a>Elementy direktivy modulu runtime
Formát souboru runtime (rd.xml) direktivy podporuje následující elementy direktivy modulu runtime. V tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) pro znázornění hierarchické.  
  
 [\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)  
 Platí zásady reflexe modulu runtime pro všechny typy používané aplikace a slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu. Toto je podřízený [ \<direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element.  
  
 [\<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Runnntime zásad platí pro všechny typy v sestavení. Toto je podřízený [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) elementy.  
  
 [\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Pokud jeho obsahující [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) – direktiva je atributem, platí zásady modulu runtime pro elementy kódu, pro které platí tento atribut.  
  
 [\<Direktivy jazyka >](../../../docs/framework/net-native/directives-element-net-native.md)  
 Kořenový element v každém souboru direktivy modulu runtime pro [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Její podřízené elementy jsou [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)  
 Platí zásady modulu runtime pro událost. Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)  
 Platí zásady modulu runtime pro pole. Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Zásady modulu runtime se vztahuje na typ parametru obecný typ nebo metoda.  
  
 [\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 Platí zásady modulu runtime pro typu, v případě, že zásada obsahující typ nebo metoda.  
  
 [\<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md)  
 Modul runtime zásad platí pro všechny typy v sestavení. Toto je podřízený [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) elementy.  
  
 [\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)  
 Platí zásady modulu runtime pro metodu. Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Sestavené obecné metody se týká zásady modulu runtime. Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Modul runtime zásad platí pro všechny typy v oboru názvů.  
  
 [\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Zásady modulu runtime se vztahuje na typ argument předaný metodě.  
  
 [\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)  
 Vlastnost se týká zásady modulu runtime. Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Modul runtime zásad platí pro všechny třídy dědí z nadřazeného typu.  
  
 [\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)  
 Platí pro typ zásady modulu runtime.  
  
 [\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Platí zásady modulu runtime pro vytvořený obecného typu.  
  
 [\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Zásady modulu runtime se vztahuje na typ zastoupený <xref:System.Type> argument předaný metodě.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubor RD.XML konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
