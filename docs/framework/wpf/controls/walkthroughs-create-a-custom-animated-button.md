---
title: 'Návod: Vytvoření tlačítka s vlastní animací'
ms.date: 03/30/2017
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
ms.openlocfilehash: aadd8ad0d37ea3736f07d3d70216278349fa26ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557105"
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="8f179-102">Návod: Vytvoření tlačítka s vlastní animací</span><span class="sxs-lookup"><span data-stu-id="8f179-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="8f179-103">Jak naznačuje název Windows Presentation Foundation (WPF) je skvělá pro díky bohaté prezentace prostředí zákazníků.</span><span class="sxs-lookup"><span data-stu-id="8f179-103">As its name suggests, Windows Presentation Foundation (WPF) is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="8f179-104">Tyto postupy ukazují, jak přizpůsobit vzhled a chování tlačítko (včetně animací).</span><span class="sxs-lookup"><span data-stu-id="8f179-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="8f179-105">Toto vlastní nastavení se provádí pomocí stylu a šablony, takže můžete použít tento vlastní tlačítko snadno na všechny tlačítka ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8f179-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="8f179-106">Následující obrázek znázorňuje tlačítko přizpůsobené, že vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="8f179-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="8f179-107">![Vlastní tlačítka, který chcete vytvořit](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="8f179-107">![The customized button that you will create](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="8f179-108">Vektorová grafika, které tvoří vzhled tlačítka se vytváří pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f179-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="8f179-109"> s výjimkou je výkonný a rozšiřitelný je podobná HTML.</span><span class="sxs-lookup"><span data-stu-id="8f179-109"> is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="8f179-110"> lze zadat ručně pomocí sady Microsoft Visual Studio nebo Poznámkový blok, nebo můžete použít visual návrh nástroje, jako je Microsoft Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="8f179-110"> can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="8f179-111">Expression Blend funguje tak, že vytvoříte základní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu, proto obě metody vytvořit stejné grafiky.</span><span class="sxs-lookup"><span data-stu-id="8f179-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f179-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8f179-112">In This Section</span></span>  
 [<span data-ttu-id="8f179-113">Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="8f179-113">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="8f179-114">Demonstruje postup vytvoření tlačítka s vlastní chování pomocí návrháře funkce Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="8f179-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="8f179-115">Vytvoření tlačítka pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="8f179-115">Create a Button by Using XAML</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="8f179-116">Ukazuje, jak vytvořit tlačítka s vlastní chování pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f179-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and Visual Studio.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8f179-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8f179-117">Related Sections</span></span>  
 [<span data-ttu-id="8f179-118">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="8f179-118">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 <span data-ttu-id="8f179-119">Popisuje, jak styly a šablony lze určit vzhled a chování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="8f179-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="8f179-120">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="8f179-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="8f179-121">Popisuje, jak může být animace objektů pomocí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animace a časování systému.</span><span class="sxs-lookup"><span data-stu-id="8f179-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="8f179-122">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="8f179-122">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="8f179-123">Popisuje, jak používat objekty štětce k vyplnění s plnou barvy, lineární přechody a paprskového přechody.</span><span class="sxs-lookup"><span data-stu-id="8f179-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="8f179-124">Přehled efektů bitmap</span><span class="sxs-lookup"><span data-stu-id="8f179-124">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="8f179-125">Popisuje účinky rastrový obrázek nepodporuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a vysvětlení způsobu jejich použití.</span><span class="sxs-lookup"><span data-stu-id="8f179-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
