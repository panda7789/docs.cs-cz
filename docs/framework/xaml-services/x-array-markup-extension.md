---
title: x:Array – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: 8acb732841aa7aaaad3e8fdd2cf2962ff44dd60b
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506069"
---
# <a name="xarray-markup-extension"></a>x:Array – rozšíření značek
Poskytuje obecné podporu pro pole objektů v XAML pomocí rozšíření kódu. To odpovídá `x:ArrayExtension` typ XAML v [MS-XAML].  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xaml
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`typeName`|Název typu, který vaše `x:Array` bude obsahovat. `typeName` může být (a často je) předponu pro XAML, obor názvů, který obsahuje XAML definice typů.|  
|`arrayContents`|Obsah položky, která je přiřazena vnitřní `ArrayExtension.Items` vlastnost. Obvykle tyto položky jsou specifikovány jako jeden nebo více elementů objektu, které jsou obsažené v `x:Array` počátečních a koncových značek. Objekty zadané tady se má být přiřaditelný k typu XAML určeného v `typeName`.|  
  
## <a name="remarks"></a>Poznámky  
 `Type` je povinný atribut pro všechny `x:Array` objektu elementy. A `Type` hodnota parametru není nutné používat `x:Type` – rozšíření značek; krátký název typu je typ, XAML, který lze zadat jako řetězec.  
  
 V implementaci rozhraní .NET Framework XAML Services, vztah mezi XAML typ vstupu a výstupu CLR <xref:System.Type> vytvořené pole je ovlivněno kontext služby pro rozšíření značek. Výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupní typ XAML po vyhledání nezbytné <xref:System.Xaml.XamlType> založené na kontext schématu XAML a <xref:System.Windows.Markup.IXamlTypeResolver> service poskytuje kontext.  
  
 Při zpracování, že je obsah pole jsou přiřazeny k `ArrayExtension.Items` vnitřní vlastnost. V <xref:System.Windows.Markup.ArrayExtension> implementace, to je reprezentována <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.  
  
 V implementaci rozhraní .NET Framework XAML Services zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.ArrayExtension> třídy. <xref:System.Windows.Markup.ArrayExtension> není zapečetěná a může použít jako základ pro implementaci rozšíření značek pro typ vlastního pole.  
  
 `x:Array` je, že informace určené pro běžné rozšiřitelnost jazyka XAML. Ale `x:Array` může také být vhodné při zadání hodnoty XAML určitých vlastností, které trvat XAML nepodporuje kolekce jako strukturované vlastnost obsah. Můžete například zadat obsah <xref:System.Collections.IEnumerable> vlastnost s `x:Array` využití.  
  
 `x:Array` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. `x:Array` výjimkou z tohoto pravidla je částečně, protože namísto zadávání alternativní atribut hodnotu zpracování, `x:Array` poskytuje alternativní zpracování její obsah vnitřní text. Díky tomuto chování může typy, které nemusí být podporovány existujícího obsahu modelu seskupeny do pole a odkazuje později v modelu code-behind díky přístupu do pojmenované pole. můžete volat <xref:System.Array> metody k získání položek jednotlivá pole.  
  
 Všechna rozšíření značek v XAML použít složené závorky ({,} `)` v syntaxi atributu, což je konvence, podle kterého na procesor XAML rozpozná, že rozšíření značek musí zpracovat hodnotu atributu. Další informace o rozšíření značek v obecné najdete v tématu [převaděče typů a rozšíření značek pro XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 V XAML 2009 `x:Array` je definován jako primitivní místo rozšíření značek jazyka. Další informace najdete v tématu [předdefinované typy obecných primitiv jazyka XAML](built-in-types-for-common-xaml-language-primitives.md).  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Obvykle elementů objektu, která naplní `x:Array` nejsou prvky, které existují v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] oboru názvů XAML a vyžadují mapování předpony oboru názvů XAML jiné než výchozí.  
  
 Například tady je jednoduchý pole dvou řetězců s `sys` předpony (a také `x`) definované na úrovni pole.  
  
```xaml
<x:Array Type="sys:String"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:sys="clr-namespace:System;assembly=mscorlib">
    <sys:String>Hello</sys:String>
    <sys:String>World</sys:String>
</x:Array>
```
  
 Pro vlastní typy, které se používají jako prvky pole musí podporovat třídu také požadavky pro instance v XAML jako elementů objektu. Další informace najdete v tématu [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
