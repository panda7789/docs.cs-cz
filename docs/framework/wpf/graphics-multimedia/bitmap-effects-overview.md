---
title: Přehled efektů bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5c304363efe7d0e9bd9e14ff916f8d852ab3a8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636013"
---
# <a name="bitmap-effects-overview"></a>Přehled efektů bitmap
Bitmapové efekty umožňují návrhářům a vývojářům aplikovat vizuální efekty na obsah vykresleného Windows Presentation Foundation (WPF). Například efekty rastrových obrázků umožňují snadno použít efekt <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> nebo efekt rozostření na obrázek nebo tlačítko.  
  
> [!IMPORTANT]
> V .NET Framework 4 nebo novější je třída <xref:System.Windows.Media.Effects.BitmapEffect> zastaralá. Pokud se pokusíte použít třídu <xref:System.Windows.Media.Effects.BitmapEffect>, obdržíte zastaralou výjimku. Nestaralá alternativa k třídě <xref:System.Windows.Media.Effects.BitmapEffect> je třída <xref:System.Windows.Media.Effects.Effect>. Ve většině případů je <xref:System.Windows.Media.Effects.Effect>á třída výrazně rychlejší.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Efekty rastrového obrázku WPF  
 Efekty rastrového obrázku (<xref:System.Windows.Media.Effects.BitmapEffect> objekt) jsou jednoduché operace zpracování v pixelech. Bitmapový efekt přebírá <xref:System.Windows.Media.Imaging.BitmapSource> jako vstup a vytvoří nový <xref:System.Windows.Media.Imaging.BitmapSource> po použití efektu, jako je rozostření nebo Vržený stín. Každý bitmapový efekt zveřejňuje vlastnosti, které mohou řídit vlastnosti filtrování, například <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Ve zvláštních případech můžete v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nastavit efekty jako vlastnosti u objektů živého <xref:System.Windows.Media.Visual>, jako je například <xref:System.Windows.Controls.Button> nebo <xref:System.Windows.Controls.TextBox>. Zpracování pixelů je použito a vykresleno v době běhu. V tomto případě se v době vykreslování <xref:System.Windows.Media.Visual> automaticky převede na svůj <xref:System.Windows.Media.Imaging.BitmapSource> ekvivalent a jako vstup do <xref:System.Windows.Media.Effects.BitmapEffect>. Výstup nahrazuje výchozí chování vykreslování objektu <xref:System.Windows.Media.Visual>. To je důvod, proč <xref:System.Windows.Media.Effects.BitmapEffect> objekty vynutit vykreslování vizuálů pouze v softwaru, což znamená, že při použití efektů nedochází k žádnému hardwarové akceleraci vizuálů.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect> simuluje objekt, který se zobrazí mimo fokus.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> vytvoří od obvodu objektu olemování barvy.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> vytvoří stín za objektem.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect> vytvoří zkosení, které vyvolá povrch obrázku v závislosti na zadané křivce.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect> vytvoří mapování hrbolů <xref:System.Windows.Media.Visual> k poskytnutí dojmu hloubky a textury z umělého světelného zdroje.  
  
> [!NOTE]
> Efekty rastrového obrázku WPF se vykreslují v softwarovém režimu. Libovolný objekt, který použije efekt, bude vykreslen také v softwaru. V případě použití rastrových efektů u velkých vizuálů nebo animování vlastností rastrového efektu se výkon snižuje. Neříkáme tomu, že byste neměli v tomto postupu používat rastrové efekty, ale měli byste pečlivě použít opatrnost a testovat, aby vaši uživatelé měli zkušenosti, které očekáváte.  
  
> [!NOTE]
> Efekty rastrového obrázku WPF nepodporují provádění částečného vztahu důvěryhodnosti. Aplikace musí mít úplná oprávnění důvěryhodnosti pro použití rastrových efektů.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Jak použít efekt  
 <xref:System.Windows.Media.Effects.BitmapEffect> je vlastnost <xref:System.Windows.Media.Visual>. Proto je použití efektů u vizuálů, například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>nebo <xref:System.Windows.UIElement>, stejně snadné jako nastavení vlastnosti. <xref:System.Windows.UIElement.BitmapEffect%2A> lze nastavit na jeden objekt <xref:System.Windows.Media.Effects.BitmapEffect> nebo lze zřetězit více efektů pomocí objektu <xref:System.Windows.Media.Effects.BitmapEffectGroup>.  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Effects.BitmapEffect> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Effects.BitmapEffect> v kódu.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Při použití <xref:System.Windows.Media.Effects.BitmapEffect> pro kontejner rozložení, jako je například <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.Canvas>, se efekt použije na vizuální strom elementu nebo vizuálu, včetně všech jeho podřízených elementů.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Vytváření vlastních efektů  
 WPF také poskytuje nespravovaná rozhraní pro vytváření vlastních efektů, které lze použít ve spravovaných aplikacích WPF. Další referenční materiály pro vytváření vlastních bitmapových efektů naleznete v dokumentaci [nespravovaného rastrového obrázku WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Nespravovaný efekt rastrového obrázku WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Přehled obrázků](imaging-overview.md)
- [Zabezpečení](../security-wpf.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
