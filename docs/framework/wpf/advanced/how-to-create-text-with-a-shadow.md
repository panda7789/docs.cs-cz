---
title: 'Postupy: Vytvoření textu se stínem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186852"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="7daab-102">Postupy: Vytvoření textu se stínem</span><span class="sxs-lookup"><span data-stu-id="7daab-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="7daab-103">Příklady v této části ukazují, jak vytvořit efekt stínu pro zobrazený text.</span><span class="sxs-lookup"><span data-stu-id="7daab-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7daab-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7daab-104">Example</span></span>  
 <span data-ttu-id="7daab-105">Objekt <xref:System.Windows.Media.Effects.DropShadowEffect> umožňuje vytvořit pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty různé efekty vrženého stínu.</span><span class="sxs-lookup"><span data-stu-id="7daab-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="7daab-106">Následující příklad ukazuje efekt vrženého stínu aplikovaný na text.</span><span class="sxs-lookup"><span data-stu-id="7daab-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="7daab-107">V tomto případě je stín měkký stín, což znamená, že barva stínu se rozostří.</span><span class="sxs-lookup"><span data-stu-id="7daab-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Textový stín s &#61; měkkosti 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 <span data-ttu-id="7daab-109">Šířku stínu můžete řídit nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7daab-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="7daab-110">Hodnota `4.0` označuje šířku stínu 4 obrazové body.</span><span class="sxs-lookup"><span data-stu-id="7daab-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="7daab-111">Měkkost nebo rozostření stínu můžete ovládat úpravou <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7daab-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="7daab-112">Hodnota `0.0` označuje žádné rozostření.</span><span class="sxs-lookup"><span data-stu-id="7daab-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="7daab-113">Následující příklad kódu ukazuje, jak vytvořit měkký stín.</span><span class="sxs-lookup"><span data-stu-id="7daab-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="7daab-114">Tyto stínové efekty neprocházejí kanálem vykreslování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] textu.</span><span class="sxs-lookup"><span data-stu-id="7daab-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="7daab-115">V důsledku toho cleartype je zakázáno při použití těchto efektů.</span><span class="sxs-lookup"><span data-stu-id="7daab-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="7daab-116">Následující příklad ukazuje efekt tíška aplikovaný na text.</span><span class="sxs-lookup"><span data-stu-id="7daab-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="7daab-117">V tomto případě není stín rozmazaný.</span><span class="sxs-lookup"><span data-stu-id="7daab-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Textový stín s &#61; měkkosti 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 <span data-ttu-id="7daab-119">Pevný stín můžete vytvořit nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> `0.0`vlastnosti na , což znamená, že se nepoužívá žádné rozostření.</span><span class="sxs-lookup"><span data-stu-id="7daab-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="7daab-120">Můžete řídit směr stínu úpravou vlastnosti. <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A></span><span class="sxs-lookup"><span data-stu-id="7daab-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="7daab-121">Nastavte směrovou hodnotu této vlastnosti `0` `360`do určité míry mezi a .</span><span class="sxs-lookup"><span data-stu-id="7daab-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="7daab-122">Následující obrázek znázorňuje směrové hodnoty nastavení vlastnosti. <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A></span><span class="sxs-lookup"><span data-stu-id="7daab-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Nastavení stupně Stínu DropShadow](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="7daab-124">Následující příklad kódu ukazuje, jak vytvořit pevný stín.</span><span class="sxs-lookup"><span data-stu-id="7daab-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="7daab-125">Použití efektu rozostření</span><span class="sxs-lookup"><span data-stu-id="7daab-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="7daab-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> lze použít k vytvoření efektu podobnéstínu, který lze umístit za textový objekt.</span><span class="sxs-lookup"><span data-stu-id="7daab-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="7daab-127">Bitmapový efekt rozostření aplikovaný na text rozostří text rovnoměrně ve všech směrech.</span><span class="sxs-lookup"><span data-stu-id="7daab-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="7daab-128">Následující příklad ukazuje efekt rozostření aplikovaný na text.</span><span class="sxs-lookup"><span data-stu-id="7daab-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Textový stín pomocí efektu BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="7daab-130">Následující příklad kódu ukazuje, jak vytvořit efekt rozostření.</span><span class="sxs-lookup"><span data-stu-id="7daab-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="7daab-131">Použití transformace překladu</span><span class="sxs-lookup"><span data-stu-id="7daab-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="7daab-132">A <xref:System.Windows.Media.TranslateTransform> lze použít k vytvoření efektu podobnéstínu, který lze umístit za textový objekt.</span><span class="sxs-lookup"><span data-stu-id="7daab-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="7daab-133">Následující příklad kódu <xref:System.Windows.Media.TranslateTransform> používá k odsazení textu.</span><span class="sxs-lookup"><span data-stu-id="7daab-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="7daab-134">V tomto příkladu vytvoří mírně odsazená kopie textu pod primárním textem stínový efekt.</span><span class="sxs-lookup"><span data-stu-id="7daab-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Stín textu pomocí TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 <span data-ttu-id="7daab-136">Následující příklad kódu ukazuje, jak vytvořit transformaci pro stínový efekt.</span><span class="sxs-lookup"><span data-stu-id="7daab-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
