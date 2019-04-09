---
title: ColorConvertedBitmap – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: e8a36a1b8592146eb2474805638cdc3697adb0c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172936"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap – rozšíření značek
Poskytuje způsob, jak určit zdroj rastrového obrázku, který nemá vložené profilů. Barva kontexty / profily jsou určena podle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], jako je zdroj obrázku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Neprofilované rastrového obrázku.|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Zdroj konfigurace profilu.|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Konfigurace cílový profil|  
  
## <a name="remarks"></a>Poznámky  
 K vyplnění související sadu hodnot vlastností zdroj bitové kopie, jako je určená tohoto rozšíření značek <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. `ColorConvertedBitmap` (nebo `ColorConvertedBitmapExtension`) nelze použít v syntax prvku vlastnosti, protože hodnoty lze nastavit pouze jako hodnoty pro počáteční konstruktor, který je řetězec následující identifikátor rozšíření.  
  
 `ColorConvertedBitmap` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Přehled obrázků](../graphics-multimedia/imaging-overview.md)
