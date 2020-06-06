---
title: Elementy direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128173"
---
# <a name="runtime-directive-elements"></a>Elementy direktivy modulu runtime
Formát souboru direktiv modulu runtime (RD. XML) podporuje následující elementy direktivy modulu runtime. Hierarchickou reprezentaci naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md) .  
  
 [\<Application>](application-element-net-native.md)  
 Aplikuje zásady odrazu modulu runtime na všechny typy používané aplikací a slouží jako kontejner pro typy celé aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu. Toto je podřízený [\<Directives>](directives-element-net-native.md) prvek elementu.  
  
 [\<Assembly>](assembly-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v sestavení. Toto je podřízený prvek [\<Application>](application-element-net-native.md) a [\<Library>](library-element-net-native.md) .  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 Pokud [\<Type>](type-element-net-native.md) je direktiva obsahující direktiva atributem, aplikace aplikuje zásady modulu runtime na prvky kódu, na které se tento atribut aplikuje.  
  
 [\<Directives>](directives-element-net-native.md)  
 Kořenový element v každém souboru direktiv modulu runtime pro .NET Native. Jeho podřízené prvky jsou [\<Application>](application-element-net-native.md) a [\<Library>](library-element-net-native.md) .  
  
 [\<Event>](event-element-net-native.md)  
 Aplikuje zásady modulu runtime na událost. Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<Field>](field-element-net-native.md)  
 Aplikuje na pole zásady modulu runtime. Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ parametru obecného typu nebo metody.  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 Aplikuje zásadu modulu runtime na typ, pokud byla tato zásada použita na obsahující typ nebo metodu.  
  
 [\<Library>](library-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v sestavení. Toto je podřízený prvek [\<Application>](application-element-net-native.md) a [\<Library>](library-element-net-native.md) .  
  
 [\<Method>](method-element-net-native.md)  
 Aplikuje zásady modulu runtime na metodu. Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 Aplikuje zásady modulu runtime na vytvořenou obecnou metodu. Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<Namespace>](namespace-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v oboru názvů.  
  
 [\<Parameter>](parameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ argumentu předaného metodě.  
  
 [\<Property>](property-element-net-native.md)  
 Aplikuje zásady modulu runtime na vlastnost. Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.  
  
 [\<Type>](type-element-net-native.md)  
 Použije zásady modulu runtime na typ.  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 Použije zásady modulu runtime na konstruovaný obecný typ.  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ reprezentovaný <xref:System.Type> argumentem předaným metodě.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace ke konfiguračnímu souboru Rd. XML](runtime-directives-rd-xml-configuration-file-reference.md)
