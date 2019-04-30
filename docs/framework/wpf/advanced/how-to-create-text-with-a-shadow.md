---
title: 'Postupy: Vytvoření textu se stínem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: a2225e297dbc0b5f9d49799cb34eb5539746e62e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776821"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="a32a2-102">Postupy: Vytvoření textu se stínem</span><span class="sxs-lookup"><span data-stu-id="a32a2-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="a32a2-103">Příklady v této části ukazují, jak vytvořit efektem stínování zobrazeného textu.</span><span class="sxs-lookup"><span data-stu-id="a32a2-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a32a2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a32a2-104">Example</span></span>  
 <span data-ttu-id="a32a2-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Objekt umožňuje vytvářet nejrůznější rozevírací efekty stínování pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="a32a2-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="a32a2-106">Následující příklad ukazuje efektem stínu použitý pro text.</span><span class="sxs-lookup"><span data-stu-id="a32a2-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="a32a2-107">V takovém případě stínové kopie je obnovitelné stínové, což znamená, že rozostření Barva stínu.</span><span class="sxs-lookup"><span data-stu-id="a32a2-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Stín Softness &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <span data-ttu-id="a32a2-109">Můžete řídit šířku stínu tak, že nastavíte <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a32a2-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="a32a2-110">Hodnota `4.0` Určuje šířku stínové 4 pixelů.</span><span class="sxs-lookup"><span data-stu-id="a32a2-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="a32a2-111">Můžete řídit Měkkost, nebo rozostření stínu tak, že upravíte <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a32a2-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="a32a2-112">Hodnota `0.0` označuje žádné rozostření.</span><span class="sxs-lookup"><span data-stu-id="a32a2-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="a32a2-113">Následující příklad kódu ukazuje, jak vytvořit obnovitelné stín.</span><span class="sxs-lookup"><span data-stu-id="a32a2-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="a32a2-114">Tyto efekty stínování se nepřenášejí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kanálu vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="a32a2-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="a32a2-115">ClearType – je zakázáno v důsledku toho při použití těchto důsledcích.</span><span class="sxs-lookup"><span data-stu-id="a32a2-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="a32a2-116">Následující příklad ukazuje pevné efektem stínu použitý pro text.</span><span class="sxs-lookup"><span data-stu-id="a32a2-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="a32a2-117">V takovém případě není rozmazávají stínu.</span><span class="sxs-lookup"><span data-stu-id="a32a2-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Stín Softness &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <span data-ttu-id="a32a2-119">Pevné stínové můžete vytvořit tak, že nastavíte <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost `0.0`, bez rozostření je používán.</span><span class="sxs-lookup"><span data-stu-id="a32a2-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="a32a2-120">Směr stínu, můžete řídit tak, že upravíte <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a32a2-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="a32a2-121">Nastavte směrové hodnotu této vlastnosti na míru mezi `0` a `360`.</span><span class="sxs-lookup"><span data-stu-id="a32a2-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="a32a2-122">Následující obrázek znázorňuje směrové hodnoty <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a32a2-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Nastavení ovládacího prvku DropShadow stupně stínu](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="a32a2-124">Následující příklad kódu ukazuje, jak vytvořit pevné stín.</span><span class="sxs-lookup"><span data-stu-id="a32a2-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="a32a2-125">Použití efektu rozostření</span><span class="sxs-lookup"><span data-stu-id="a32a2-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="a32a2-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> slouží k vytvoření efektu stínové jako, který je možné použít za objekt textu.</span><span class="sxs-lookup"><span data-stu-id="a32a2-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="a32a2-127">Bitmapový efekt rozostření použitý pro text rozostří text rovnoměrně ve všech směrech.</span><span class="sxs-lookup"><span data-stu-id="a32a2-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="a32a2-128">Následující příklad ukazuje efekt rozostření použitý pro text.</span><span class="sxs-lookup"><span data-stu-id="a32a2-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Pomocí BlurBitmapEffect Stín textu](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="a32a2-130">Následující příklad kódu ukazuje, jak vytvořit rozostření efekt.</span><span class="sxs-lookup"><span data-stu-id="a32a2-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="a32a2-131">Použití transformace Translace</span><span class="sxs-lookup"><span data-stu-id="a32a2-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="a32a2-132">A <xref:System.Windows.Media.TranslateTransform> slouží k vytvoření efektu stínové jako, který je možné použít za objekt textu.</span><span class="sxs-lookup"><span data-stu-id="a32a2-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="a32a2-133">Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> odsazení textu.</span><span class="sxs-lookup"><span data-stu-id="a32a2-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="a32a2-134">V tomto příkladu vytvoří kopii mírně posunu text pod primární text efektem stínování.</span><span class="sxs-lookup"><span data-stu-id="a32a2-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Stín textu pomocí TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 <span data-ttu-id="a32a2-136">Následující příklad kódu ukazuje, jak vytvořit transformace pro efektem stínování.</span><span class="sxs-lookup"><span data-stu-id="a32a2-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
