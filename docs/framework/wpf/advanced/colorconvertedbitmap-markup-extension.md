---
title: ColorConvertedBitmap – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: a5b491723a036c1b1fd0bb61736e6f2ee53fbcd3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141218"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap – rozšíření značek
Poskytuje způsob, jak určit zdroj rastrového obrázku, který nemá vložený profil. Kontexty barev/profily jsou určeny identifikátorem URI, jako je identifikátor URI zdroje obrázku.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`imageSource`|Identifikátor URI neprofilované bitmapy.|  
|`sourceIIC`|Identifikátor URI konfigurace zdrojového profilu.|  
|`destinationIIC`|Identifikátor URI konfigurace cílového profilu|  
  
## <a name="remarks"></a>Poznámky  
 Tato přípona označení je určena k naplnění související sady hodnot vlastností zdroje obrázku, jako <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>je.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. `ColorConvertedBitmap`(nebo `ColorConvertedBitmapExtension`) nelze použít v syntaxi elementu Property, protože hodnoty lze nastavit pouze jako hodnoty na počátečním konstruktoru, což je řetězec následující po identifikátoru rozšíření.  
  
 `ColorConvertedBitmap`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Přehled obrázků](../graphics-multimedia/imaging-overview.md)
