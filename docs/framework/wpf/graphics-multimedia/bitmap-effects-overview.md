---
title: Přehled efektů bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5e73f21d4ce4988f56c139d13038dca902b5b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186994"
---
# <a name="bitmap-effects-overview"></a>Přehled efektů bitmap
Bitmapové efekty umožňují návrhářům a vývojářům aplikovat vizuální efekty na vykreslený obsah WPF (Windows Presentation Foundation). Bitmapové efekty například umožňují <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> snadno aplikovat efekt nebo efekt rozostření na obraz nebo tlačítko.  
  
> [!IMPORTANT]
> V rozhraní .NET Framework 4 <xref:System.Windows.Media.Effects.BitmapEffect> nebo novější je třída zastaralá. Pokud se pokusíte <xref:System.Windows.Media.Effects.BitmapEffect> použít třídu, získáte zastaralou výjimku. Nezastaralá alternativa <xref:System.Windows.Media.Effects.BitmapEffect> ke <xref:System.Windows.Media.Effects.Effect> třídě je třída. Ve většině situací <xref:System.Windows.Media.Effects.Effect> je třída výrazně rychlejší.  

<a name="wpf_effects"></a>
## <a name="wpf-bitmap-effects"></a>Bitmapové efekty WPF  
 Bitmapové<xref:System.Windows.Media.Effects.BitmapEffect> efekty ( objekt) jsou jednoduché operace zpracování obrazových bodů. Bitmapový efekt <xref:System.Windows.Media.Imaging.BitmapSource> se projeví jako vstup <xref:System.Windows.Media.Imaging.BitmapSource> a po aplikování efektu vytvoří nový efekt, například rozostření nebo vržený stín. Každý bitmapový efekt zpřístupňuje vlastnosti, které <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>mohou řídit vlastnosti filtrování, například .  
  
 Jako zvláštní případ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]v , efekty lze <xref:System.Windows.Media.Visual> nastavit jako vlastnosti na živé objekty, například <xref:System.Windows.Controls.Button> nebo . <xref:System.Windows.Controls.TextBox> Zpracování pixelů je použito a vykresleno za běhu. V tomto případě je v době <xref:System.Windows.Media.Visual> vykreslování a automaticky převedena na ekvivalentní <xref:System.Windows.Media.Imaging.BitmapSource> a je vložena jako vstup do . <xref:System.Windows.Media.Effects.BitmapEffect> Výstup nahradí výchozí <xref:System.Windows.Media.Visual> chování vykreslování objektu. To je <xref:System.Windows.Media.Effects.BitmapEffect> důvod, proč objekty nutí vizuály k vykreslení pouze v softwaru, tj.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>simuluje objekt, který se jeví jako nezaostřený.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>vytvoří aureoly barvy po obvodu objektu.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>vytvoří stín za objektem.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>vytvoří zle, který zvedne povrch obrazu podle zadané křivky.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>vytváří mapování hrbolů <xref:System.Windows.Media.Visual> a, aby působilo jako hloubka a textura z umělého světelného zdroje.  
  
> [!NOTE]
> Bitmapové efekty WPF jsou vykreslovány v softwarovém režimu. Jakýkoli objekt, který použije efekt, bude také vykreslen v softwaru. Výkon je nejvíce snížen při použití bitmapových efektů na velké vizuály nebo animování vlastností bitmapového efektu. To neznamená, že byste neměli používat bitmapové efekty tímto způsobem vůbec, ale měli byste používat opatrně a důkladně otestovat, aby zajistily, že vaši uživatelé jsou stále zkušenosti, které očekáváte.  
  
> [!NOTE]
> Bitmapové efekty WPF nepodporují částečné spuštění důvěryhodnosti. Aplikace musí mít oprávnění úplné důvěryhodnosti, aby mohla používat bitmapové efekty.  
  
<a name="applyeffects"></a>
## <a name="how-to-apply-an-effect"></a>Jak aplikovat efekt  
 <xref:System.Windows.Media.Effects.BitmapEffect>je vlastnost <xref:System.Windows.Media.Visual>na . Proto použití efektů na vizuální <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Image>prvky, například , , <xref:System.Windows.Media.DrawingVisual>, nebo <xref:System.Windows.UIElement>, je stejně snadné jako nastavení vlastnosti. <xref:System.Windows.UIElement.BitmapEffect%2A>lze nastavit na <xref:System.Windows.Media.Effects.BitmapEffect> jeden objekt nebo pomocí objektu <xref:System.Windows.Media.Effects.BitmapEffectGroup> lze zřetězit více efektů.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.Effects.BitmapEffect> použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]v .  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.Effects.BitmapEffect> použít v kódu.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Pokud <xref:System.Windows.Media.Effects.BitmapEffect> je použita na kontejner <xref:System.Windows.Controls.DockPanel> rozložení, jako je například nebo <xref:System.Windows.Controls.Canvas>, efekt se použije na vizuální strom prvku nebo vizuálu, včetně všech jeho podřízených prvků.  
  
<a name="customeffects"></a>
## <a name="creating-custom-effects"></a>Vytváření vlastních efektů  
 WPF také poskytuje nespravované rozhraní pro vytvoření vlastních efektů, které lze použít ve spravovaných aplikacích WPF. Další referenční materiál pro vytváření vlastních bitmapových efektů naleznete v dokumentaci [k nespravovanému bitmapovému efektu WPF.](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Nespravovaný bitmapový efekt WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Přehled obrázků](imaging-overview.md)
- [Zabezpečení](../security-wpf.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
