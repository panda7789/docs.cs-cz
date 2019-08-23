---
title: 'Postupy: Vytvoření textu se stínem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960442"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="d9190-102">Postupy: Vytvoření textu se stínem</span><span class="sxs-lookup"><span data-stu-id="d9190-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="d9190-103">Příklady v této části ukazují, jak vytvořit stínový efekt pro zobrazený text.</span><span class="sxs-lookup"><span data-stu-id="d9190-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9190-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9190-104">Example</span></span>  
 <span data-ttu-id="d9190-105">Objekt umožňuje vytvořit celou řadu efektů vržených stínů pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty. <xref:System.Windows.Media.Effects.DropShadowEffect></span><span class="sxs-lookup"><span data-stu-id="d9190-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="d9190-106">Následující příklad ukazuje efekt Vržený stín aplikovaný na text.</span><span class="sxs-lookup"><span data-stu-id="d9190-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="d9190-107">V tomto případě je stín měkký stín, což znamená, že se barva stínu rozostří.</span><span class="sxs-lookup"><span data-stu-id="d9190-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Stín textu s měkkou &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <span data-ttu-id="d9190-109">Šířku stínu můžete nastavit nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d9190-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="d9190-110">Hodnota `4.0` označuje stínovou šířku 4 pixelů.</span><span class="sxs-lookup"><span data-stu-id="d9190-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="d9190-111">Úpravou <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnosti můžete řídit měkké nebo rozostření stínové kopie.</span><span class="sxs-lookup"><span data-stu-id="d9190-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="d9190-112">Hodnota `0.0` označuje rozostření.</span><span class="sxs-lookup"><span data-stu-id="d9190-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="d9190-113">Následující příklad kódu ukazuje, jak vytvořit měkký stín.</span><span class="sxs-lookup"><span data-stu-id="d9190-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="d9190-114">Tyto efekty [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stínů neprojde kanálem vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="d9190-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="d9190-115">V důsledku toho je technologie ClearType při použití těchto efektů zakázaná.</span><span class="sxs-lookup"><span data-stu-id="d9190-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="d9190-116">Následující příklad ukazuje efekt vrženého stínu, který je použit na text.</span><span class="sxs-lookup"><span data-stu-id="d9190-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="d9190-117">V tomto případě není stín rozmazaný.</span><span class="sxs-lookup"><span data-stu-id="d9190-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Stín textu s přítvrdosti &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <span data-ttu-id="d9190-119">Můžete vytvořit pevný stín <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> nastavením vlastnosti na `0.0`, což znamená, že se nepoužívá žádná rozostření.</span><span class="sxs-lookup"><span data-stu-id="d9190-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="d9190-120">Změnou <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> vlastnosti můžete řídit směr stínu.</span><span class="sxs-lookup"><span data-stu-id="d9190-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="d9190-121">Nastavte směrovou hodnotu této vlastnosti na stupeň mezi `0` a. `360`</span><span class="sxs-lookup"><span data-stu-id="d9190-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="d9190-122">Následující ilustrace znázorňuje směrové hodnoty <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d9190-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Nastavení DropShadow úrovně stínu](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="d9190-124">Následující příklad kódu ukazuje, jak vytvořit pevný stín.</span><span class="sxs-lookup"><span data-stu-id="d9190-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="d9190-125">Použití efektu rozostření</span><span class="sxs-lookup"><span data-stu-id="d9190-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="d9190-126"><xref:System.Windows.Media.Effects.BlurBitmapEffect> Lze použít k vytvoření efektu stínu, který lze umístit za textový objekt.</span><span class="sxs-lookup"><span data-stu-id="d9190-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="d9190-127">Efekt rozostření rastrového obrázku aplikovaný na text rozostří text rovnoměrně ze všech směrů.</span><span class="sxs-lookup"><span data-stu-id="d9190-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="d9190-128">Následující příklad ukazuje efekt rozostření aplikovaný na text.</span><span class="sxs-lookup"><span data-stu-id="d9190-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Stín textu s použitím BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="d9190-130">Následující příklad kódu ukazuje, jak vytvořit efekt rozostření.</span><span class="sxs-lookup"><span data-stu-id="d9190-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="d9190-131">Použití transformace převodu</span><span class="sxs-lookup"><span data-stu-id="d9190-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="d9190-132"><xref:System.Windows.Media.TranslateTransform> Lze použít k vytvoření efektu stínu, který lze umístit za textový objekt.</span><span class="sxs-lookup"><span data-stu-id="d9190-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="d9190-133">Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunu textu.</span><span class="sxs-lookup"><span data-stu-id="d9190-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="d9190-134">V tomto příkladu mírně posunutí kopie textu pod primárním textem vytvoří stínový efekt.</span><span class="sxs-lookup"><span data-stu-id="d9190-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Stín textu s použitím TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 <span data-ttu-id="d9190-136">Následující příklad kódu ukazuje, jak vytvořit transformaci pro stínový efekt.</span><span class="sxs-lookup"><span data-stu-id="d9190-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
