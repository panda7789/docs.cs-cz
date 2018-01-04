---
title: "ColorConvertedBitmap – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df6fac332f20d64ddf6569554a75ef96a5536c0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap – rozšíření značek
Poskytuje způsob, jak zadat zdroj rastrový obrázek, který nemá vložený profil. Barva kontexty / profily jsou určené [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], jako je zdroj bitové kopie [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Nonprofiled bitmapy.|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Zdroj konfigurace profilu.|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Cílové konfigurace profilu|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozšíření značek slouží k vyplnění související sadu hodnot vlastností zdroj bitové kopie, jako <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. `ColorConvertedBitmap`(nebo `ColorConvertedBitmapExtension`) nelze použít v syntaxi element vlastnost, protože hodnoty lze nastavit pouze hodnoty na počáteční konstruktor, který je řetězec, následující identifikátor rozšíření.  
  
 `ColorConvertedBitmap`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v jejich syntaxi atributů, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Přehled obrázků](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
