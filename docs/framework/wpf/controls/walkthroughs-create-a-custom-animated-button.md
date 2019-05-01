---
title: 'Návody: Vytvoření tlačítka s vlastní animací'
ms.date: 03/30/2017
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
ms.openlocfilehash: 3c601641a0eb1024722b4f449f0ab23e54fe93dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024466"
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="d8c53-102">Návody: Vytvoření tlačítka s vlastní animací</span><span class="sxs-lookup"><span data-stu-id="d8c53-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="d8c53-103">Jak název napovídá, se skvěle hodí pro provedení bohatý prezentační prostředí pro zákazníky, kteří Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d8c53-103">As its name suggests, Windows Presentation Foundation (WPF) is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="d8c53-104">Tyto podrobné postupy vám ukážou, jak přizpůsobit vzhled a chování tlačítka (včetně animacích).</span><span class="sxs-lookup"><span data-stu-id="d8c53-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="d8c53-105">Toto přizpůsobení se provádí pomocí stylu a šablon, takže můžete provést toto tlačítko Vlastní snadno u tlačítka ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d8c53-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="d8c53-106">Následující obrázek znázorňuje vlastní tlačítko, které vytvoří.</span><span class="sxs-lookup"><span data-stu-id="d8c53-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="d8c53-107">![Vlastní tlačítka, které vytvoříte](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="d8c53-107">![The customized button that you will create](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="d8c53-108">Vektorové grafiky, které tvoří vzhled tlačítka jsou vytvářeny instalační sadou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8c53-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="d8c53-109">je podobný HTML, s výjimkou je výkonný a rozšiřitelný.</span><span class="sxs-lookup"><span data-stu-id="d8c53-109">is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="d8c53-110">lze napsat ručně pomocí sady Microsoft Visual Studio nebo programu Poznámkový blok, nebo můžete použít návrhové nástroje, jako je Microsoft Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="d8c53-110">can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="d8c53-111">Expression Blend funguje tak, že vytvoříte základní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu tak, že obě metody vytvoření stejné grafiky.</span><span class="sxs-lookup"><span data-stu-id="d8c53-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8c53-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d8c53-112">In This Section</span></span>  
 [<span data-ttu-id="d8c53-113">Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="d8c53-113">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="d8c53-114">Popisuje způsob vytvoření tlačítka s vlastní chování pomocí návrháře funkcí Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="d8c53-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="d8c53-115">Vytvoření tlačítka pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="d8c53-115">Create a Button by Using XAML</span></span>](walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="d8c53-116">Popisuje způsob vytvoření tlačítka s vlastní chování pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8c53-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and Visual Studio.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8c53-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d8c53-117">Related Sections</span></span>  
 [<span data-ttu-id="d8c53-118">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d8c53-118">Styling and Templating</span></span>](styling-and-templating.md)  
 <span data-ttu-id="d8c53-119">Popisuje, jak – styly a šablony lze určit vzhled a chování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="d8c53-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="d8c53-120">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="d8c53-120">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="d8c53-121">Popisuje, jak lze pomocí animovat objekty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animace a časování systému.</span><span class="sxs-lookup"><span data-stu-id="d8c53-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="d8c53-122">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="d8c53-122">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="d8c53-123">Popisuje způsob použití štětce objekty pro malování plnými barvami, lineární přechody a radiálními přechody.</span><span class="sxs-lookup"><span data-stu-id="d8c53-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="d8c53-124">Přehled efektů bitmap</span><span class="sxs-lookup"><span data-stu-id="d8c53-124">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="d8c53-125">Popisuje bitmapových efektů nepodporuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a vysvětluje, jak aplikovat.</span><span class="sxs-lookup"><span data-stu-id="d8c53-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
