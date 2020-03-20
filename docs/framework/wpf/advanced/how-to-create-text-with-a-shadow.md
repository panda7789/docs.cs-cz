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
# <a name="how-to-create-text-with-a-shadow"></a>Postupy: Vytvoření textu se stínem
Příklady v této části ukazují, jak vytvořit efekt stínu pro zobrazený text.  
  
## <a name="example"></a>Příklad  
 Objekt <xref:System.Windows.Media.Effects.DropShadowEffect> umožňuje vytvořit pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty různé efekty vrženého stínu. Následující příklad ukazuje efekt vrženého stínu aplikovaný na text. V tomto případě je stín měkký stín, což znamená, že barva stínu se rozostří.  
  
 ![Textový stín s &#61; měkkosti 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 Šířku stínu můžete řídit nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnosti. Hodnota `4.0` označuje šířku stínu 4 obrazové body. Měkkost nebo rozostření stínu můžete ovládat úpravou <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnosti. Hodnota `0.0` označuje žádné rozostření. Následující příklad kódu ukazuje, jak vytvořit měkký stín.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Tyto stínové efekty neprocházejí kanálem vykreslování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] textu. V důsledku toho cleartype je zakázáno při použití těchto efektů.  
  
 Následující příklad ukazuje efekt tíška aplikovaný na text. V tomto případě není stín rozmazaný.  
  
 ![Textový stín s &#61; měkkosti 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 Pevný stín můžete vytvořit nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> `0.0`vlastnosti na , což znamená, že se nepoužívá žádné rozostření. Můžete řídit směr stínu úpravou vlastnosti. <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> Nastavte směrovou hodnotu této vlastnosti `0` `360`do určité míry mezi a . Následující obrázek znázorňuje směrové hodnoty nastavení vlastnosti. <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>  
  
 ![Nastavení stupně Stínu DropShadow](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 Následující příklad kódu ukazuje, jak vytvořit pevný stín.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Použití efektu rozostření  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> lze použít k vytvoření efektu podobnéstínu, který lze umístit za textový objekt. Bitmapový efekt rozostření aplikovaný na text rozostří text rovnoměrně ve všech směrech.  
  
 Následující příklad ukazuje efekt rozostření aplikovaný na text.  
  
 ![Textový stín pomocí efektu BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 Následující příklad kódu ukazuje, jak vytvořit efekt rozostření.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Použití transformace překladu  
 A <xref:System.Windows.Media.TranslateTransform> lze použít k vytvoření efektu podobnéstínu, který lze umístit za textový objekt.  
  
 Následující příklad kódu <xref:System.Windows.Media.TranslateTransform> používá k odsazení textu. V tomto příkladu vytvoří mírně odsazená kopie textu pod primárním textem stínový efekt.  
  
 ![Stín textu pomocí TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 Následující příklad kódu ukazuje, jak vytvořit transformaci pro stínový efekt.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
