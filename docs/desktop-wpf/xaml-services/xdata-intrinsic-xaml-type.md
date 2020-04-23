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
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071540"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData – vnitřní typ jazyka XAML
Umožňuje umístění datových ostrovů XML v rámci výroby XAML. Xml prvky uvnitř `x:XData` by neměly být zpracovány procesory XAML, jako by byly součástí výchozího oboru názvů XAML nebo jiného oboru názvů XAML. `x:XData`může obsahovat libovolný dobře formátovaný XML.

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
|`elementDataRoot`|Jediný kořenový prvek uzavřeného datového ostrova. Pro většinu případných spotřebitelů xml, který nemá jeden kořen je považován za neplatný. Zejména jeden kořen je vyžadován, `x:XData` pokud je určen jako zdroj dat XML pro WPF nebo mnoho dalších technologií, které používají zdroje XML pro datové vazby.|
|`[elementData]`|Nepovinný parametr. XML, který představuje data XML. Libovolný počet prvků může být obsažen jako data prvku a vnořené prvky mohou být obsaženy v jiných prvcích; platí však obecná pravidla XML.|

## <a name="remarks"></a>Poznámky

Elementy XML `x:XData` v objektu mohou znovu deklarovat všechny možné obory názvů a předpony obsahujícího objektu XMLDOM v rámci dat.

Programový přístup k datům XML a `x:XData` vnitřnímu typu XAML je možný <xref:System.Windows.Markup.XData> ve službách .NET XAML prostřednictvím třídy.

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

Objekt `x:XData` se používá především jako podřízený <xref:System.Windows.Data.XmlDataProvider>objekt , nebo alternativně jako <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> podřízený objekt vlastnosti (v XAML, to je obvykle vyjádřeno v syntaxi elementu vlastnosti).

Data by měla obvykle předefinovat základní obor názvů XML v rámci datového ostrova jako nový výchozí obor názvů XML (nastavený na prázdný řetězec). To je nejjednodušší pro jednoduché <xref:System.Windows.Data.Binding.XPath%2A> datové ostrovy, protože výrazy, které se používají k odkazování a vazbě na data, se mohou vyhnout zahrnutí předpon. Složitější datové ostrovy mohou definovat více předpon pro data a použít určitou předponu pro obor názvů XML v kořenovém adresáři. V takovém případě <xref:System.Windows.Data.Binding.XPath%2A> by všechny odkazy na výrazy měly obsahovat příslušnou předponu mapovanou oborem názvů. Další informace naleznete v [tématu Přehled datových vazeb](../data/data-binding-overview.md).

Technicky, `x:XData` může být použit jako obsah <xref:System.Xml.Serialization.IXmlSerializable>jakékoliv vlastnosti typu . Je <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> však jedinou významnou implementací.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Data.XmlDataProvider>
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Rozšíření značek připojení](../../framework/wpf/advanced/binding-markup-extension.md)
