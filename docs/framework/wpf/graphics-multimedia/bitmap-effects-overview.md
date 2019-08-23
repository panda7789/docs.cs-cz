---
title: Přehled efektů bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: f2fa42d5d63cad6a71efd259416dad3416bf2d72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935303"
---
# <a name="bitmap-effects-overview"></a>Přehled efektů bitmap
Bitmapové efekty umožňují návrhářům a vývojářům aplikovat vizuální efekty na obsah vykresleného Windows Presentation Foundation (WPF). Například efekty rastrových obrázků umožňují snadno aplikovat <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efekt nebo efekt rozostření na obrázek nebo tlačítko.  
  
> [!IMPORTANT]
> V .NET Framework 4 nebo novější <xref:System.Windows.Media.Effects.BitmapEffect> třída je zastaralá. Pokud se pokusíte použít <xref:System.Windows.Media.Effects.BitmapEffect> třídu, obdržíte zastaralou výjimku. Nestaralá alternativa <xref:System.Windows.Media.Effects.BitmapEffect> třídy <xref:System.Windows.Media.Effects.Effect> je třída. Ve většině případů je tato <xref:System.Windows.Media.Effects.Effect> třída výrazně rychlejší.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Efekty rastrového obrázku WPF  
 Rastrové efekty<xref:System.Windows.Media.Effects.BitmapEffect> (objekt) jsou jednoduché operace zpracování v pixelech. Bitmapový efekt přebírá <xref:System.Windows.Media.Imaging.BitmapSource> jako vstup a vytvoří nový <xref:System.Windows.Media.Imaging.BitmapSource> po použití efektu, jako je rozostření nebo Vržený stín. Každý bitmapový efekt zveřejňuje vlastnosti, které mohou řídit vlastnosti filtrování, například <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> z <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zvláštní případ lze v systému nastavit jako vlastnosti pro živé <xref:System.Windows.Media.Visual> objekty, jako je <xref:System.Windows.Controls.Button> například nebo <xref:System.Windows.Controls.TextBox>. Zpracování pixelů je použito a vykresleno v době běhu. V tomto případě <xref:System.Windows.Media.Visual> je v době vykreslování automaticky převeden na jeho <xref:System.Windows.Media.Imaging.BitmapSource> ekvivalent a je <xref:System.Windows.Media.Effects.BitmapEffect>zadáván jako vstup do. Výstup nahradí <xref:System.Windows.Media.Visual> výchozí chování vykreslování objektu. To je důvod <xref:System.Windows.Media.Effects.BitmapEffect> , proč objekty vynutí vykreslování vizuálů pouze v softwaru, což znamená, že při použití efektů nedochází k žádnému hardwarové akceleraci vizuálů.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>simuluje objekt, který se zobrazí mimo fokus.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>Vytvoří olemování barvy kolem obvodu objektu.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>vytvoří stín za objektem.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>Vytvoří zkosení, které vyvolá povrch obrázku v závislosti na zadané křivce.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>Vytvoří mapování <xref:System.Windows.Media.Visual> hrbolů pro poskytnutí dojmu hloubky a textury z umělého světelného zdroje.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Bitmapové efekty se vykreslují v softwarovém režimu. Libovolný objekt, který použije efekt, bude vykreslen také v softwaru. V případě použití rastrových efektů u velkých vizuálů nebo animování vlastností rastrového efektu se výkon snižuje. Neříkáme tomu, že byste neměli v tomto postupu používat rastrové efekty, ale měli byste pečlivě použít opatrnost a testovat, aby vaši uživatelé měli zkušenosti, které očekáváte.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]efekty rastrového obrázku nepodporují spouštění částečného vztahu důvěryhodnosti. Aplikace musí mít úplná oprávnění důvěryhodnosti pro použití rastrových efektů.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Jak použít efekt  
 <xref:System.Windows.Media.Effects.BitmapEffect>je vlastnost v <xref:System.Windows.Media.Visual>. Proto použití efektů u <xref:System.Windows.Controls.Button>vizuálů, jako je <xref:System.Windows.Media.DrawingVisual>, <xref:System.Windows.Controls.Image>, nebo <xref:System.Windows.UIElement>, je stejně snadné jako nastavení vlastnosti. <xref:System.Windows.UIElement.BitmapEffect%2A>lze nastavit na jeden <xref:System.Windows.Media.Effects.BitmapEffect> objekt nebo více efektů lze zřetězit <xref:System.Windows.Media.Effects.BitmapEffectGroup> pomocí objektu.  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Effects.BitmapEffect> v. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Effects.BitmapEffect> kód v kódu.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Když je použit na kontejner rozložení, <xref:System.Windows.Controls.DockPanel> například nebo <xref:System.Windows.Controls.Canvas>, efekt je aplikován na vizuální strom prvku nebo vizuálu, včetně všech jeho podřízených prvků. <xref:System.Windows.Media.Effects.BitmapEffect>  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Vytváření vlastních efektů  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]poskytuje také nespravovaná rozhraní k vytváření vlastních efektů, které lze použít [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve spravovaných aplikacích. Další referenční materiály pro vytváření vlastních bitmapových efektů naleznete v dokumentaci [nespravovaného rastrového obrázku WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Nespravovaný efekt rastrového obrázku WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Přehled obrázků](imaging-overview.md)
- [Zabezpečení](../security-wpf.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
