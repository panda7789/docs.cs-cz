---
title: 'Postupy: Vytvoření textu se stínem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 1b7740284afcda6eab41fb68be3b4a2f032cc77d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544755"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="2c55d-102">Postupy: Vytvoření textu se stínem</span><span class="sxs-lookup"><span data-stu-id="2c55d-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="2c55d-103">Příklady v této části ukazují, jak vytvořit efekt stínu pro zobrazený text.</span><span class="sxs-lookup"><span data-stu-id="2c55d-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c55d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c55d-104">Example</span></span>  
 <span data-ttu-id="2c55d-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Objekt umožňuje vytvořit stínové důsledky pro celou řadu rozevírací [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="2c55d-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="2c55d-106">Následující příklad ukazuje efekt stínu rozevírací použít na text.</span><span class="sxs-lookup"><span data-stu-id="2c55d-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="2c55d-107">V takovém případě stínové kopie je logicky shadow, což znamená rozostření barvu stínu.</span><span class="sxs-lookup"><span data-stu-id="2c55d-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="2c55d-108">![Stín textu zobrazovat Softness &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="2c55d-108">![Text shadow with Softness &#61; 0.25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="2c55d-109">Příklad textu logicky stínové</span><span class="sxs-lookup"><span data-stu-id="2c55d-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="2c55d-110">Můžete řídit šířku stínu nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2c55d-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="2c55d-111">Hodnota `4.0` Určuje šířku stínové 4 pixelů.</span><span class="sxs-lookup"><span data-stu-id="2c55d-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="2c55d-112">Můžete řídit Měkkost, nebo rozostření stínu změnou <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2c55d-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="2c55d-113">Hodnota `0.0` označuje bez rozostření.</span><span class="sxs-lookup"><span data-stu-id="2c55d-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="2c55d-114">Následující příklad kódu ukazuje, jak vytvořit logicky stínové.</span><span class="sxs-lookup"><span data-stu-id="2c55d-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="2c55d-115">Tyto důsledky stínové se nepřenášejí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kanálu vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="2c55d-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="2c55d-116">V důsledku toho ClearType vypnutá při použití těchto důsledcích.</span><span class="sxs-lookup"><span data-stu-id="2c55d-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="2c55d-117">Následující příklad ukazuje efekt stínu pevný rozevírací použít na text.</span><span class="sxs-lookup"><span data-stu-id="2c55d-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="2c55d-118">V takovém případě se bude stín hranice.</span><span class="sxs-lookup"><span data-stu-id="2c55d-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="2c55d-119">![Stín textu zobrazovat Softness &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="2c55d-119">![Text shadow with Softness &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="2c55d-120">Příklad textu pevný stínové</span><span class="sxs-lookup"><span data-stu-id="2c55d-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="2c55d-121">Můžete vytvořit pevný stínové nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost `0.0`, což naznačuje, že se používá bez rozostření.</span><span class="sxs-lookup"><span data-stu-id="2c55d-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="2c55d-122">Směr stínu, můžete řídit úpravou <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2c55d-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="2c55d-123">Nastavte směrovou hodnotu této vlastnosti na určitý stupeň mezi `0` a `360`.</span><span class="sxs-lookup"><span data-stu-id="2c55d-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="2c55d-124">Následující obrázek znázorňuje směrovou hodnoty <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2c55d-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="2c55d-125">![Nastavení stupně DropShadow stínu](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="2c55d-125">![DropShadow degree setting of shadow](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="2c55d-126">Směr DropShadow diagram</span><span class="sxs-lookup"><span data-stu-id="2c55d-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="2c55d-127">Následující příklad kódu ukazuje, jak vytvořit pevný stínové.</span><span class="sxs-lookup"><span data-stu-id="2c55d-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="2c55d-128">Pomocí efekt rozostření</span><span class="sxs-lookup"><span data-stu-id="2c55d-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="2c55d-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> slouží k vytvoření efekt stínové jako, který se může za objekt textu.</span><span class="sxs-lookup"><span data-stu-id="2c55d-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="2c55d-130">Efekt rozostření rastrový obrázek použít na text rozostří text rovnoměrně ve všech pokynů.</span><span class="sxs-lookup"><span data-stu-id="2c55d-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="2c55d-131">Následující příklad ukazuje efekt rozostření použít na text.</span><span class="sxs-lookup"><span data-stu-id="2c55d-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="2c55d-132">![Stín textu zobrazovat pomocí BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="2c55d-132">![Text shadow using a BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="2c55d-133">Příklad textu efekt rozostření</span><span class="sxs-lookup"><span data-stu-id="2c55d-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="2c55d-134">Následující příklad kódu ukazuje, jak vytvořit efekt rozostření.</span><span class="sxs-lookup"><span data-stu-id="2c55d-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="2c55d-135">Pomocí přeložit transformace</span><span class="sxs-lookup"><span data-stu-id="2c55d-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="2c55d-136">A <xref:System.Windows.Media.TranslateTransform> slouží k vytvoření efekt stínové jako, který se může za objekt textu.</span><span class="sxs-lookup"><span data-stu-id="2c55d-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="2c55d-137">Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunutí textu.</span><span class="sxs-lookup"><span data-stu-id="2c55d-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="2c55d-138">V tomto příkladu se vytvoří kopii text pod primární text mírně posunutí efekt stínu.</span><span class="sxs-lookup"><span data-stu-id="2c55d-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="2c55d-139">![Stín textu zobrazovat pomocí TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="2c55d-139">![Text shadow using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="2c55d-140">Příklad použití transformace pro přidání stínu textu</span><span class="sxs-lookup"><span data-stu-id="2c55d-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="2c55d-141">Následující příklad kódu ukazuje, jak vytvořit transformace pro přidání stínu.</span><span class="sxs-lookup"><span data-stu-id="2c55d-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
