---
title: x:XData – vnitřní typ jazyka XAML
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053701"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData – vnitřní typ jazyka XAML
Umožňuje umístění datových ostrovů XML v rámci výroby XAML. Prvky XML v `x:XData` rámci by neměly být zpracovány pomocí procesorů XAML, jako by se jednalo o součást působícího výchozího oboru názvů XAML nebo jakýkoli jiný obor názvů XAML. `x:XData`může obsahovat libovolný kód ve správném formátu.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`elementDataRoot`|Jeden kořenový prvek vloženého datového ostrova. Pro většinu případných uživatelů se XML, který nemá jeden kořenový adresář, považuje za neplatnou. Konkrétně je vyžadován jeden kořenový adresář, pokud `x:XData` je určen jako zdroj dat XML pro WPF nebo mnoho dalších technologií, které používají zdroje XML pro datovou vazbu.|  
|`[elementData]`|Volitelný parametr. XML, který představuje data XML. Libovolný počet prvků může být obsažen jako data elementu a vnořené prvky mohou být obsaženy v jiných prvcích; platí ale obecná pravidla XML.|  
  
## <a name="remarks"></a>Poznámky  
 Prvky XML v rámci `x:XData` objektu mohou znovu deklarovat všechny možné obory názvů a předpony obsahujícího XMLDOM v rámci dat.  
  
 Programový přístup k datům XML a `x:XData` vnitřní typ XAML je možný v .NET Framework služby XAML <xref:System.Windows.Markup.XData> prostřednictvím třídy.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Objekt je primárně použit jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider>pro nebo nebo jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> vlastnosti (v jazyce XAML, je obvykle vyjádřen v syntaxi elementu vlastnosti). `x:XData`  
  
 Data by obvykle předefinovala základní obor názvů XML v datovém ostrůvku tak, aby byl nový výchozí obor názvů XML (nastavený na prázdný řetězec). To je nejjednodušší pro jednoduché datové ostrůvky, <xref:System.Windows.Data.Binding.XPath%2A> protože výrazy, které se používají k odkazování na data a vázání na ně, se můžou vyhnout zahrnutí předpon. Složitější datové ostrůvky mohou definovat více předpon pro data a použít konkrétní předponu pro obor názvů XML v kořenu. V tomto případě by měly <xref:System.Windows.Data.Binding.XPath%2A> všechny odkazy na výrazy zahrnovat příslušnou předponu mapované oboru názvů. Další informace najdete v tématu [Přehled datových vazeb](../wpf/data/data-binding-overview.md).  
  
 Technicky, `x:XData` lze použít jako obsah libovolné vlastnosti typu <xref:System.Xml.Serialization.IXmlSerializable>. <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> Je však jedinou významnou implementací.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.XmlDataProvider>
- [Přehled datových vazeb](../wpf/data/data-binding-overview.md)
- [Rozšíření značek datové vazby](../wpf/advanced/binding-markup-extension.md)
