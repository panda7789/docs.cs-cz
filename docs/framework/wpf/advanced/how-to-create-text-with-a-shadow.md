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
# <a name="how-to-create-text-with-a-shadow"></a>Postupy: Vytvoření textu se stínem
Příklady v této části ukazují, jak vytvořit efektem stínování zobrazeného textu.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Effects.DropShadowEffect> Objekt umožňuje vytvářet nejrůznější rozevírací efekty stínování pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty. Následující příklad ukazuje efektem stínu použitý pro text. V takovém případě stínové kopie je obnovitelné stínové, což znamená, že rozostření Barva stínu.  
  
 ![Stín Softness &#61; 0,25](./media/shadowtext01.jpg "ShadowText01")  
Příklad textu se stínem obnovitelně  
  
 Můžete řídit šířku stínu tak, že nastavíte <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnost. Hodnota `4.0` Určuje šířku stínové 4 pixelů. Můžete řídit Měkkost, nebo rozostření stínu tak, že upravíte <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost. Hodnota `0.0` označuje žádné rozostření. Následující příklad kódu ukazuje, jak vytvořit obnovitelné stín.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Tyto efekty stínování se nepřenášejí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kanálu vykreslování textu. ClearType – je zakázáno v důsledku toho při použití těchto důsledcích.  
  
 Následující příklad ukazuje pevné efektem stínu použitý pro text. V takovém případě není rozmazávají stínu.  
  
 ![Stín Softness &#61; 0](./media/shadowtext02.jpg "ShadowText02")  
Příklad textu se stínem pevný  
  
 Pevné stínové můžete vytvořit tak, že nastavíte <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost `0.0`, bez rozostření je používán. Směr stínu, můžete řídit tak, že upravíte <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> vlastnost. Nastavte směrové hodnotu této vlastnosti na míru mezi `0` a `360`. Následující obrázek znázorňuje směrové hodnoty <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> nastavení vlastnosti.  
  
 ![Nastavení ovládacího prvku DropShadow stupně stínu](./media/shadowtext08.png "ShadowText08")  
Směr ovládacího prvku DropShadow diagramu  
  
 Následující příklad kódu ukazuje, jak vytvořit pevné stín.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Použití efektu rozostření  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> slouží k vytvoření efektu stínové jako, který je možné použít za objekt textu. Bitmapový efekt rozostření použitý pro text rozostří text rovnoměrně ve všech směrech.  
  
 Následující příklad ukazuje efekt rozostření použitý pro text.  
  
 ![Stín textu pomocí BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")  
Příklad text s efektem rozostření  
  
 Následující příklad kódu ukazuje, jak vytvořit rozostření efekt.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Použití transformace Translace  
 A <xref:System.Windows.Media.TranslateTransform> slouží k vytvoření efektu stínové jako, který je možné použít za objekt textu.  
  
 Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> odsazení textu. V tomto příkladu vytvoří kopii mírně posunu text pod primární text efektem stínování.  
  
 ![Stín textu pomocí TranslateTransform](./media/shadowtext07.jpg "ShadowText07")  
Příklad pro efektem stínování pomocí transformace textu  
  
 Následující příklad kódu ukazuje, jak vytvořit transformace pro efektem stínování.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
