---
title: "Postupy: Vytvoření textu se stínem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bbc3da54c10304e52f93d38365a8d9ed005505
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="de1b7-102">Postupy: Vytvoření textu se stínem</span><span class="sxs-lookup"><span data-stu-id="de1b7-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="de1b7-103">Příklady v této části ukazují, jak vytvořit efekt stínu pro zobrazený text.</span><span class="sxs-lookup"><span data-stu-id="de1b7-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de1b7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="de1b7-104">Example</span></span>  
 <span data-ttu-id="de1b7-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Objekt umožňuje vytvořit stínové důsledky pro celou řadu rozevírací [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="de1b7-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="de1b7-106">Následující příklad ukazuje efekt stínu rozevírací použít na text.</span><span class="sxs-lookup"><span data-stu-id="de1b7-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="de1b7-107">V takovém případě stínové kopie je logicky shadow, což znamená rozostření barvu stínu.</span><span class="sxs-lookup"><span data-stu-id="de1b7-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="de1b7-108">![Stín textu zobrazovat s Měkkost & č. 61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="de1b7-108">![Text shadow with Softness &#61; 0.25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="de1b7-109">Příklad textu logicky stínové</span><span class="sxs-lookup"><span data-stu-id="de1b7-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="de1b7-110">Můžete řídit šířku stínu nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="de1b7-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="de1b7-111">Hodnota `4.0` Určuje šířku stínové 4 pixelů.</span><span class="sxs-lookup"><span data-stu-id="de1b7-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="de1b7-112">Můžete řídit Měkkost, nebo rozostření stínu změnou <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="de1b7-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="de1b7-113">Hodnota `0.0` označuje bez rozostření.</span><span class="sxs-lookup"><span data-stu-id="de1b7-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="de1b7-114">Následující příklad kódu ukazuje, jak vytvořit logicky stínové.</span><span class="sxs-lookup"><span data-stu-id="de1b7-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="de1b7-115">Tyto důsledky stínové se nepřenášejí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kanálu vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="de1b7-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="de1b7-116">V důsledku toho ClearType vypnutá při použití těchto důsledcích.</span><span class="sxs-lookup"><span data-stu-id="de1b7-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="de1b7-117">Následující příklad ukazuje efekt stínu pevný rozevírací použít na text.</span><span class="sxs-lookup"><span data-stu-id="de1b7-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="de1b7-118">V takovém případě se bude stín hranice.</span><span class="sxs-lookup"><span data-stu-id="de1b7-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="de1b7-119">![Stín textu zobrazovat s Měkkost & č. 61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="de1b7-119">![Text shadow with Softness &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="de1b7-120">Příklad textu pevný stínové</span><span class="sxs-lookup"><span data-stu-id="de1b7-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="de1b7-121">Můžete vytvořit pevný stínové nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost `0.0`, což naznačuje, že se používá bez rozostření.</span><span class="sxs-lookup"><span data-stu-id="de1b7-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="de1b7-122">Směr stínu, můžete řídit úpravou <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="de1b7-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="de1b7-123">Nastavte směrovou hodnotu této vlastnosti na určitý stupeň mezi `0` a `360`.</span><span class="sxs-lookup"><span data-stu-id="de1b7-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="de1b7-124">Následující obrázek znázorňuje směrovou hodnoty <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="de1b7-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="de1b7-125">![Nastavení stupně DropShadow stínu](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="de1b7-125">![DropShadow degree setting of shadow](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="de1b7-126">Směr DropShadow diagram</span><span class="sxs-lookup"><span data-stu-id="de1b7-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="de1b7-127">Následující příklad kódu ukazuje, jak vytvořit pevný stínové.</span><span class="sxs-lookup"><span data-stu-id="de1b7-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="de1b7-128">Pomocí efekt rozostření</span><span class="sxs-lookup"><span data-stu-id="de1b7-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="de1b7-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> slouží k vytvoření efekt stínové jako, který se může za objekt textu.</span><span class="sxs-lookup"><span data-stu-id="de1b7-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="de1b7-130">Efekt rozostření rastrový obrázek použít na text rozostří text rovnoměrně ve všech pokynů.</span><span class="sxs-lookup"><span data-stu-id="de1b7-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="de1b7-131">Následující příklad ukazuje efekt rozostření použít na text.</span><span class="sxs-lookup"><span data-stu-id="de1b7-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="de1b7-132">![Stín textu zobrazovat pomocí BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="de1b7-132">![Text shadow using a BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="de1b7-133">Příklad textu efekt rozostření</span><span class="sxs-lookup"><span data-stu-id="de1b7-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="de1b7-134">Následující příklad kódu ukazuje, jak vytvořit efekt rozostření.</span><span class="sxs-lookup"><span data-stu-id="de1b7-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="de1b7-135">Pomocí přeložit transformace</span><span class="sxs-lookup"><span data-stu-id="de1b7-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="de1b7-136">A <xref:System.Windows.Media.TranslateTransform> slouží k vytvoření efekt stínové jako, který se může za objekt textu.</span><span class="sxs-lookup"><span data-stu-id="de1b7-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="de1b7-137">Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunutí textu.</span><span class="sxs-lookup"><span data-stu-id="de1b7-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="de1b7-138">V tomto příkladu se vytvoří kopii text pod primární text mírně posunutí efekt stínu.</span><span class="sxs-lookup"><span data-stu-id="de1b7-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="de1b7-139">![Stín textu zobrazovat pomocí TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="de1b7-139">![Text shadow using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="de1b7-140">Příklad použití transformace pro přidání stínu textu</span><span class="sxs-lookup"><span data-stu-id="de1b7-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="de1b7-141">Následující příklad kódu ukazuje, jak vytvořit transformace pro přidání stínu.</span><span class="sxs-lookup"><span data-stu-id="de1b7-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
