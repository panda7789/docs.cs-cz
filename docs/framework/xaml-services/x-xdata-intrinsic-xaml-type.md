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
ms.openlocfilehash: c8044bc341ded6ef7b03bbdf701e724654460d54
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125156"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData – vnitřní typ jazyka XAML
Umožňuje umístění datové ostrůvky XML v rámci výrobní XAML. Elementy XML v rámci `x:XData` by neměla být zpracována XAML procesorů, jako by šlo část funguje výchozí obor názvů XAML nebo libovolný jiný obor názvů XAML. `x:XData` může obsahovat libovolný XML ve správném formátu.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`elementDataRoot`|Jeden kořenový element uzavřený dat ostrov. Pro většinu konečné spotřebitele se považuje za neplatný kód XML, který nemá jeden kořenový. Jeden kořenový je konkrétně vyžadováno, pokud `x:XData` je určený jako XML použitého jako zdroj dat pro WPF nebo mnoho technologií, které používají zdroje XML pro datovou vazbu.|  
|`[elementData]`|Volitelné. Soubor XML, který představuje XML data. Libovolný počet prvků, které mohou být obsaženy jako prvek dat a vnořené elementy mohou být obsaženy v dalších prvků; však platí obecná pravidla XML.|  
  
## <a name="remarks"></a>Poznámky  
 Elementy XML v rámci `x:XData` objekt lze znovu deklarovat všechny možné obory názvů a předpony obsahující XMLDOM v datech.  
  
 Programový přístup k datům XML a `x:XData` vnitřního typu XAML je možné v rozhraní .NET Framework XAML Services prostřednictvím <xref:System.Windows.Markup.XData> třídy.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 `x:XData` Objektu se používá především jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider>, nebo jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> vlastnost (v XAML, to je obvykle vyjádřeny syntax prvku vlastnosti).  
  
 Data by měly předefinovat obvykle základního oboru názvů XML v rámci dat ostrov jako nové výchozí XML obor názvů (nastavenou na prázdný řetězec). Toto je nejjednodušší pro jednoduchou datovou ostrovy, protože <xref:System.Windows.Data.Binding.XPath%2A> výrazy, které se používají k odkazu a vytvořit vazbu na data se můžete vyhnout zahrnutí předpony. Komplexnější datové ostrůvky může definovat více předpony pro data a použít konkrétní předponu pro obor názvů XML v kořenovém adresáři. V takovém případě všechny <xref:System.Windows.Data.Binding.XPath%2A> výraz odkazuje by měla zahrnovat příslušné mapované na obor názvů předponu. Další informace najdete v tématu [přehled datových vazeb](../wpf/data/data-binding-overview.md).  
  
 Technicky vzato `x:XData` může sloužit jako obsah libovolnou vlastnost typu <xref:System.Xml.Serialization.IXmlSerializable>. Ale <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> pouze viditelného implementaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.XmlDataProvider>
- [Přehled datových vazeb](../wpf/data/data-binding-overview.md)
- [Rozšíření značek připojení](../wpf/advanced/binding-markup-extension.md)
