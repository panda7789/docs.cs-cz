---
title: 'Postupy: Vytvoření textu se stínem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 4d200aa980e8f2e6d22291669dfb07db54a5f0c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370670"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="8675d-102">Postupy: Vytvoření textu se stínem</span><span class="sxs-lookup"><span data-stu-id="8675d-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="8675d-103">Příklady v této části ukazují, jak vytvořit efektem stínování zobrazeného textu.</span><span class="sxs-lookup"><span data-stu-id="8675d-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8675d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8675d-104">Example</span></span>  
 <span data-ttu-id="8675d-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Objekt umožňuje vytvářet nejrůznější rozevírací efekty stínování pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="8675d-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="8675d-106">Následující příklad ukazuje efektem stínu použitý pro text.</span><span class="sxs-lookup"><span data-stu-id="8675d-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="8675d-107">V takovém případě stínové kopie je obnovitelné stínové, což znamená, že rozostření Barva stínu.</span><span class="sxs-lookup"><span data-stu-id="8675d-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="8675d-108">![Stín Softness &#61; 0,25](./media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="8675d-108">![Text shadow with Softness &#61; 0.25](./media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="8675d-109">Příklad textu se stínem obnovitelně</span><span class="sxs-lookup"><span data-stu-id="8675d-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="8675d-110">Můžete řídit šířku stínu tak, že nastavíte <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8675d-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="8675d-111">Hodnota `4.0` Určuje šířku stínové 4 pixelů.</span><span class="sxs-lookup"><span data-stu-id="8675d-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="8675d-112">Můžete řídit Měkkost, nebo rozostření stínu tak, že upravíte <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8675d-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="8675d-113">Hodnota `0.0` označuje žádné rozostření.</span><span class="sxs-lookup"><span data-stu-id="8675d-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="8675d-114">Následující příklad kódu ukazuje, jak vytvořit obnovitelné stín.</span><span class="sxs-lookup"><span data-stu-id="8675d-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="8675d-115">Tyto efekty stínování se nepřenášejí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kanálu vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="8675d-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="8675d-116">ClearType – je zakázáno v důsledku toho při použití těchto důsledcích.</span><span class="sxs-lookup"><span data-stu-id="8675d-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="8675d-117">Následující příklad ukazuje pevné efektem stínu použitý pro text.</span><span class="sxs-lookup"><span data-stu-id="8675d-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="8675d-118">V takovém případě není rozmazávají stínu.</span><span class="sxs-lookup"><span data-stu-id="8675d-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="8675d-119">![Stín Softness &#61; 0](./media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="8675d-119">![Text shadow with Softness &#61; 0](./media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="8675d-120">Příklad textu se stínem pevný</span><span class="sxs-lookup"><span data-stu-id="8675d-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="8675d-121">Pevné stínové můžete vytvořit tak, že nastavíte <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost `0.0`, bez rozostření je používán.</span><span class="sxs-lookup"><span data-stu-id="8675d-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="8675d-122">Směr stínu, můžete řídit tak, že upravíte <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8675d-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="8675d-123">Nastavte směrové hodnotu této vlastnosti na míru mezi `0` a `360`.</span><span class="sxs-lookup"><span data-stu-id="8675d-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="8675d-124">Následující obrázek znázorňuje směrové hodnoty <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8675d-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="8675d-125">![Nastavení ovládacího prvku DropShadow stupně stínu](./media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="8675d-125">![DropShadow degree setting of shadow](./media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="8675d-126">Směr ovládacího prvku DropShadow diagramu</span><span class="sxs-lookup"><span data-stu-id="8675d-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="8675d-127">Následující příklad kódu ukazuje, jak vytvořit pevné stín.</span><span class="sxs-lookup"><span data-stu-id="8675d-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="8675d-128">Použití efektu rozostření</span><span class="sxs-lookup"><span data-stu-id="8675d-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="8675d-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> slouží k vytvoření efektu stínové jako, který je možné použít za objekt textu.</span><span class="sxs-lookup"><span data-stu-id="8675d-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="8675d-130">Bitmapový efekt rozostření použitý pro text rozostří text rovnoměrně ve všech směrech.</span><span class="sxs-lookup"><span data-stu-id="8675d-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="8675d-131">Následující příklad ukazuje efekt rozostření použitý pro text.</span><span class="sxs-lookup"><span data-stu-id="8675d-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="8675d-132">![Stín textu pomocí BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="8675d-132">![Text shadow using a BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="8675d-133">Příklad text s efektem rozostření</span><span class="sxs-lookup"><span data-stu-id="8675d-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="8675d-134">Následující příklad kódu ukazuje, jak vytvořit rozostření efekt.</span><span class="sxs-lookup"><span data-stu-id="8675d-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="8675d-135">Použití transformace Translace</span><span class="sxs-lookup"><span data-stu-id="8675d-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="8675d-136">A <xref:System.Windows.Media.TranslateTransform> slouží k vytvoření efektu stínové jako, který je možné použít za objekt textu.</span><span class="sxs-lookup"><span data-stu-id="8675d-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="8675d-137">Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> odsazení textu.</span><span class="sxs-lookup"><span data-stu-id="8675d-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="8675d-138">V tomto příkladu vytvoří kopii mírně posunu text pod primární text efektem stínování.</span><span class="sxs-lookup"><span data-stu-id="8675d-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="8675d-139">![Stín textu pomocí TranslateTransform](./media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="8675d-139">![Text shadow using a TranslateTransform](./media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="8675d-140">Příklad pro efektem stínování pomocí transformace textu</span><span class="sxs-lookup"><span data-stu-id="8675d-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="8675d-141">Následující příklad kódu ukazuje, jak vytvořit transformace pro efektem stínování.</span><span class="sxs-lookup"><span data-stu-id="8675d-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
