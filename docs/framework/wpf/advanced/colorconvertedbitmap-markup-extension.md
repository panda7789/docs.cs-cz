---
title: ColorConvertedBitmap – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 7d14ddc6276b9dd7baee12e267e8af1250bc11ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582772"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap – rozšíření značek
Poskytuje způsob, jak určit zdroj rastrového obrázku, který nemá vložený profil. Kontexty barev/profily jsou určeny identifikátorem URI, jako je identifikátor URI zdroje obrázku.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`imageSource`|Identifikátor URI neprofilované bitmapy.|  
|`sourceIIC`|Identifikátor URI konfigurace zdrojového profilu.|  
|`destinationIIC`|Identifikátor URI konfigurace cílového profilu|  
  
## <a name="remarks"></a>Poznámky  
 Tato přípona označení je určena k naplnění související sady hodnot zdrojové vlastnosti obrázku, například <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. `ColorConvertedBitmap` (nebo `ColorConvertedBitmapExtension`) nelze použít v syntaxi elementu vlastnosti, protože hodnoty lze nastavit pouze jako hodnoty na počátečním konstruktoru, což je řetězec následující po identifikátoru rozšíření.  
  
 `ColorConvertedBitmap` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznává, že rozšíření značek musí zpracovat atribut. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Přehled obrázků](../graphics-multimedia/imaging-overview.md)
