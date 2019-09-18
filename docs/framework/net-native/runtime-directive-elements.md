---
title: Elementy direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062f13ad92f37bb7ae29ed34dcf88f99f98e7612
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049273"
---
# <a name="runtime-directive-elements"></a>Elementy direktivy modulu runtime
Formát souboru direktiv modulu runtime (RD. XML) podporuje následující elementy direktivy modulu runtime. Hierarchickou reprezentaci naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md) .  
  
 [\<> Aplikace](application-element-net-native.md)  
 Aplikuje zásady odrazu modulu runtime na všechny typy používané aplikací a slouží jako kontejner pro typy celé aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu. Toto je podřízený [ \<prvek direktiv >](directives-element-net-native.md) elementu.  
  
 [\<> Sestavení](assembly-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v sestavení. Toto je podřízený objekt [ \<aplikace >](application-element-net-native.md) a [ \<> prvků knihovny](library-element-net-native.md) .  
  
 [\<AttributeImplies >](attributeimplies-element-net-native.md)  
 Pokud je jeho nadřazeným [ \<typem](type-element-net-native.md) direktiva > atribut, aplikuje zásady modulu runtime na prvky kódu, na které se tento atribut aplikuje.  
  
 [\<> Direktiv](directives-element-net-native.md)  
 Kořenový element v každém souboru direktiv modulu runtime pro .NET Native. Jeho podřízené prvky jsou [ \<aplikace >](application-element-net-native.md) a [ \<> knihovny](library-element-net-native.md).  
  
 [\<> Události](event-element-net-native.md)  
 Aplikuje zásady modulu runtime na událost. Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.  
  
 [\<> Pole](field-element-net-native.md)  
 Aplikuje na pole zásady modulu runtime. Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.  
  
 [\<GenericParameter >](genericparameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ parametru obecného typu nebo metody.  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 Aplikuje zásadu modulu runtime na typ, pokud byla tato zásada použita na obsahující typ nebo metodu.  
  
 [\<Library>](library-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v sestavení. Toto je podřízený objekt [ \<aplikace >](application-element-net-native.md) a [ \<> prvků knihovny](library-element-net-native.md) .  
  
 [\<Method>](method-element-net-native.md)  
 Aplikuje zásady modulu runtime na metodu. Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 Aplikuje zásady modulu runtime na vytvořenou obecnou metodu. Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.  
  
 [\<Namespace>](namespace-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v oboru názvů.  
  
 [\<> Parametru](parameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ argumentu předaného metodě.  
  
 [\<> Vlastnosti](property-element-net-native.md)  
 Aplikuje zásady modulu runtime na vlastnost. Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.  
  
 [\<> Podtypů](subtypes-element-net-native.md)  
 Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.  
  
 [\<Zadejte >](type-element-net-native.md)  
 Použije zásady modulu runtime na typ.  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 Použije zásady modulu runtime na konstruovaný obecný typ.  
  
 [\<TypeParameter >](typeparameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ reprezentovaný <xref:System.Type> argumentem předaným metodě.  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace ke konfiguračnímu souboru Rd. XML](runtime-directives-rd-xml-configuration-file-reference.md)
