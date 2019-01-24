---
title: Elementy direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52800b204873604d927193e1280f2eb6ccbcce0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638363"
---
# <a name="runtime-directive-elements"></a>Elementy direktivy modulu runtime
Formát souboru modulu runtime (rd.xml) direktivy podporuje následující elementy direktivy modulu runtime. Zobrazit [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) pro Hierarchická reprezentace.  
  
 [\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)  
 Platí pro všechny typy, které aplikace používá zásady reflexe modulu runtime a slouží jako kontejner pro celou aplikaci typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu. To je podřízeným prvkem [ \<direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) elementu.  
  
 [\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Zásady modulu runtime se vztahuje na všechny typy v sestavení. To je podřízeným prvkem [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md) elementy.  
  
 [\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Pokud specifikací [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) – direktiva je atributu, platí zásady modulu runtime pro prvky kódu, u kterých je tento atribut použitá.  
  
 [\<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md)  
 Kořenový element v každém souboru direktiv modulu runtime pro [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Jeho podřízené prvky jsou [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Event>](../../../docs/framework/net-native/event-element-net-native.md)  
 Zásady modulu runtime se vztahuje na událost. To je podřízeným prvkem [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<pole >](../../../docs/framework/net-native/field-element-net-native.md)  
 Zásady modulu runtime se vztahuje na pole. To je podřízeným prvkem [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Použije zásady na modul runtime na typ parametru obecného typu nebo metody.  
  
 [\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 Použije zásady modulu runtime na typ, pokud tyto zásady se nastavily pro nadřazený typ nebo metoda.  
  
 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)  
 Zásady modulu runtime se vztahuje na všechny typy v sestavení. To je podřízeným prvkem [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md) elementy.  
  
 [\<Method>](../../../docs/framework/net-native/method-element-net-native.md)  
 Zásady modulu runtime se vztahuje na metodu. To je podřízeným prvkem [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Použije zásady modulu runtime konstruovanou obecnou metodu. To je podřízeným prvkem [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Zásady modulu runtime se vztahuje na všechny typy v oboru názvů.  
  
 [\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Použije zásady modulu runtime typu argument předaný metodě.  
  
 [\<Property>](../../../docs/framework/net-native/property-element-net-native.md)  
 Vlastnost se týká zásady modulu runtime. To je podřízeným prvkem [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.  
  
 [\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Zásady modulu runtime se vztahuje na všechny třídy dědí z nadřazeného typu.  
  
 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)  
 Použije zásady modulu runtime typu.  
  
 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Platí pro Konstruovaný obecný typ zásady modulu runtime.  
  
 [\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Zásady modulu runtime se vztahuje na typ zastoupený <xref:System.Type> argument předaný metodě.  
  
## <a name="see-also"></a>Viz také:
- [Odkaz na soubor RD.XML, které konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
