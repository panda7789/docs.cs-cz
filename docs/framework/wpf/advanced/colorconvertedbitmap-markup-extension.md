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
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="c6a21-102">ColorConvertedBitmap – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="c6a21-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="c6a21-103">Poskytuje způsob, jak určit zdroj rastrového obrázku, který nemá vložený profil.</span><span class="sxs-lookup"><span data-stu-id="c6a21-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="c6a21-104">Kontexty barev/profily jsou určeny identifikátorem URI, jako je identifikátor URI zdroje obrázku.</span><span class="sxs-lookup"><span data-stu-id="c6a21-104">Color contexts / profiles are specified by URI, as is the image source URI.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c6a21-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="c6a21-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c6a21-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="c6a21-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="c6a21-107">Identifikátor URI neprofilované bitmapy.</span><span class="sxs-lookup"><span data-stu-id="c6a21-107">The URI of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="c6a21-108">Identifikátor URI konfigurace zdrojového profilu.</span><span class="sxs-lookup"><span data-stu-id="c6a21-108">The URI of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="c6a21-109">Identifikátor URI konfigurace cílového profilu</span><span class="sxs-lookup"><span data-stu-id="c6a21-109">The URI of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6a21-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6a21-110">Remarks</span></span>  
 <span data-ttu-id="c6a21-111">Tato přípona označení je určena k naplnění související sady hodnot vlastností zdroje obrázku, jako <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>je.</span><span class="sxs-lookup"><span data-stu-id="c6a21-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="c6a21-112">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="c6a21-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="c6a21-113">`ColorConvertedBitmap`(nebo `ColorConvertedBitmapExtension`) nelze použít v syntaxi elementu Property, protože hodnoty lze nastavit pouze jako hodnoty na počátečním konstruktoru, což je řetězec následující po identifikátoru rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c6a21-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="c6a21-114">`ColorConvertedBitmap`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="c6a21-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="c6a21-115">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c6a21-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="c6a21-116">Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="c6a21-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="c6a21-117">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c6a21-117">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a21-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6a21-118">See also</span></span>

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="c6a21-119">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c6a21-119">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="c6a21-120">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="c6a21-120">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
