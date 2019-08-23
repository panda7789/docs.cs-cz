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
# <a name="how-to-create-text-with-a-shadow"></a>Postupy: Vytvoření textu se stínem
Příklady v této části ukazují, jak vytvořit stínový efekt pro zobrazený text.  
  
## <a name="example"></a>Příklad  
 Objekt umožňuje vytvořit celou řadu efektů vržených stínů pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty. <xref:System.Windows.Media.Effects.DropShadowEffect> Následující příklad ukazuje efekt Vržený stín aplikovaný na text. V tomto případě je stín měkký stín, což znamená, že se barva stínu rozostří.  
  
 ![Stín textu s měkkou &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 Šířku stínu můžete nastavit nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnosti. Hodnota `4.0` označuje stínovou šířku 4 pixelů. Úpravou <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnosti můžete řídit měkké nebo rozostření stínové kopie. Hodnota `0.0` označuje rozostření. Následující příklad kódu ukazuje, jak vytvořit měkký stín.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Tyto efekty [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stínů neprojde kanálem vykreslování textu. V důsledku toho je technologie ClearType při použití těchto efektů zakázaná.  
  
 Následující příklad ukazuje efekt vrženého stínu, který je použit na text. V tomto případě není stín rozmazaný.  
  
 ![Stín textu s přítvrdosti &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 Můžete vytvořit pevný stín <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> nastavením vlastnosti na `0.0`, což znamená, že se nepoužívá žádná rozostření. Změnou <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> vlastnosti můžete řídit směr stínu. Nastavte směrovou hodnotu této vlastnosti na stupeň mezi `0` a. `360` Následující ilustrace znázorňuje směrové hodnoty <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> nastavení vlastnosti.  
  
 ![Nastavení DropShadow úrovně stínu](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 Následující příklad kódu ukazuje, jak vytvořit pevný stín.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Použití efektu rozostření  
 <xref:System.Windows.Media.Effects.BlurBitmapEffect> Lze použít k vytvoření efektu stínu, který lze umístit za textový objekt. Efekt rozostření rastrového obrázku aplikovaný na text rozostří text rovnoměrně ze všech směrů.  
  
 Následující příklad ukazuje efekt rozostření aplikovaný na text.  
  
 ![Stín textu s použitím BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 Následující příklad kódu ukazuje, jak vytvořit efekt rozostření.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Použití transformace převodu  
 <xref:System.Windows.Media.TranslateTransform> Lze použít k vytvoření efektu stínu, který lze umístit za textový objekt.  
  
 Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunu textu. V tomto příkladu mírně posunutí kopie textu pod primárním textem vytvoří stínový efekt.  
  
 ![Stín textu s použitím TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 Následující příklad kódu ukazuje, jak vytvořit transformaci pro stínový efekt.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
