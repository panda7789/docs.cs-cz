---
title: ColorConvertedBitmap – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: e8a36a1b8592146eb2474805638cdc3697adb0c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172936"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="89385-102">ColorConvertedBitmap – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="89385-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="89385-103">Poskytuje způsob, jak určit zdroj rastrového obrázku, který nemá vložené profilů.</span><span class="sxs-lookup"><span data-stu-id="89385-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="89385-104">Barva kontexty / profily jsou určena podle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], jako je zdroj obrázku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89385-104">Color contexts / profiles are specified by [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], as is the image source [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="89385-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="89385-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="89385-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="89385-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="89385-107">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Neprofilované rastrového obrázku.</span><span class="sxs-lookup"><span data-stu-id="89385-107">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="89385-108">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Zdroj konfigurace profilu.</span><span class="sxs-lookup"><span data-stu-id="89385-108">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="89385-109">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Konfigurace cílový profil</span><span class="sxs-lookup"><span data-stu-id="89385-109">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89385-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89385-110">Remarks</span></span>  
 <span data-ttu-id="89385-111">K vyplnění související sadu hodnot vlastností zdroj bitové kopie, jako je určená tohoto rozšíření značek <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="89385-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="89385-112">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="89385-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="89385-113">`ColorConvertedBitmap` (nebo `ColorConvertedBitmapExtension`) nelze použít v syntax prvku vlastnosti, protože hodnoty lze nastavit pouze jako hodnoty pro počáteční konstruktor, který je řetězec následující identifikátor rozšíření.</span><span class="sxs-lookup"><span data-stu-id="89385-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="89385-114">`ColorConvertedBitmap` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="89385-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="89385-115">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="89385-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="89385-116">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="89385-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="89385-117">Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="89385-117">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89385-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89385-118">See also</span></span>

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="89385-119">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="89385-119">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="89385-120">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="89385-120">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
