---
title: Elementy direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128173"
---
# <a name="runtime-directive-elements"></a>Elementy direktivy modulu runtime
Formát souboru direktiv modulu runtime (RD. XML) podporuje následující elementy direktivy modulu runtime. Hierarchickou reprezentaci naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md) .  
  
 [\<> aplikace](application-element-net-native.md)  
 Aplikuje zásady odrazu modulu runtime na všechny typy používané aplikací a slouží jako kontejner pro typy celé aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu. Toto je podřízený prvek [direktiv\<](directives-element-net-native.md) elementu.  
  
 [\<> sestavení](assembly-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v sestavení. Toto je podřízený prvek [\<aplikace >](application-element-net-native.md) a\<prvky [> knihovny](library-element-net-native.md) .  
  
 [\<AttributeImplies >](attributeimplies-element-net-native.md)  
 Pokud je v něm obsažená direktiva [typu\<](type-element-net-native.md) je atribut, aplikuje zásady modulu runtime na prvky kódu, na které se tento atribut aplikuje.  
  
 [Direktivy \<](directives-element-net-native.md)  
 Kořenový element v každém souboru direktiv modulu runtime pro .NET Native. Jeho podřízené prvky jsou [\<aplikační >](application-element-net-native.md) a [\<knihovny >](library-element-net-native.md).  
  
 [> události \<](event-element-net-native.md)  
 Aplikuje zásady modulu runtime na událost. Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .  
  
 [\<pole >](field-element-net-native.md)  
 Aplikuje na pole zásady modulu runtime. Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .  
  
 [\<GenericParameter >](genericparameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ parametru obecného typu nebo metody.  
  
 [\<ImpliesType >](impliestype-element-net-native.md)  
 Aplikuje zásadu modulu runtime na typ, pokud byla tato zásada použita na obsahující typ nebo metodu.  
  
 [> knihovny \<](library-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v sestavení. Toto je podřízený prvek [\<aplikace >](application-element-net-native.md) a\<prvky [> knihovny](library-element-net-native.md) .  
  
 [Metoda\<](method-element-net-native.md)  
 Aplikuje zásady modulu runtime na metodu. Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .  
  
 [\<MethodInstantiation >](methodinstantiation-element-net-native.md)  
 Aplikuje zásady modulu runtime na vytvořenou obecnou metodu. Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .  
  
 [Obor názvů \<](namespace-element-net-native.md)  
 Použije zásady modulu runtime pro všechny typy v oboru názvů.  
  
 [Parametr \<](parameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ argumentu předaného metodě.  
  
 [Vlastnost \<](property-element-net-native.md)  
 Aplikuje zásady modulu runtime na vlastnost. Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .  
  
 [\<podtypy >](subtypes-element-net-native.md)  
 Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.  
  
 [Typ\<](type-element-net-native.md)  
 Použije zásady modulu runtime na typ.  
  
 [\<TypeInstantiation >](typeinstantiation-element-net-native.md)  
 Použije zásady modulu runtime na konstruovaný obecný typ.  
  
 [\<TypeParameter >](typeparameter-element-net-native.md)  
 Aplikuje zásady modulu runtime na typ reprezentovaný argumentem <xref:System.Type> předaným metodě.  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace ke konfiguračnímu souboru Rd. XML](runtime-directives-rd-xml-configuration-file-reference.md)
