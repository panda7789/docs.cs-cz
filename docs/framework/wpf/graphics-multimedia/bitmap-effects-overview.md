---
title: Přehled efektů bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 97b878621d5aa1860cd955755d9bbc344b95b993
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032566"
---
# <a name="bitmap-effects-overview"></a>Přehled efektů bitmap
Bitmapové efekty povolit návrháři a vývojáři použít vizuální efekty k vykreslení obsahu Windows Presentation Foundation (WPF). Například bitmapových efektů umožňují snadno použít <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> vliv nebo rozostření mohou mít vliv na bitovou kopii nebo tlačítko.  
  
> [!IMPORTANT]
>  V [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] nebo novější, <xref:System.Windows.Media.Effects.BitmapEffect> třída je zastaralá. Pokud se pokusíte použít <xref:System.Windows.Media.Effects.BitmapEffect> třídy, obdržíte výjimku zastaralé. Nezastaralou alternativou k <xref:System.Windows.Media.Effects.BitmapEffect> třída je <xref:System.Windows.Media.Effects.Effect> třídy. Ve většině případů <xref:System.Windows.Media.Effects.Effect> třída je výrazně rychlejší.  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Bitmapové efekty WPF  
 Bitmapové efekty (<xref:System.Windows.Media.Effects.BitmapEffect> objekt) jsou jednoduché pixel operace zpracování. Bitmapový efekt přijímá <xref:System.Windows.Media.Imaging.BitmapSource> jako vstup a vytvoří novou <xref:System.Windows.Media.Imaging.BitmapSource> po použití účinek, jako je například stínem rozostření nebo drop. Každý rastrový efekt zpřístupní vlastnosti, které můžete řídit filtrování vlastností, jako například <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> z <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Ve speciálním případě v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], účinky lze nastavit jako vlastnosti na živé <xref:System.Windows.Media.Visual> objekty, například <xref:System.Windows.Controls.Button> nebo <xref:System.Windows.Controls.TextBox>. Zpracování pixel se použije a vykreslí v době běhu. V takovém případě v době vykreslování <xref:System.Windows.Media.Visual> je automaticky převedena na jeho <xref:System.Windows.Media.Imaging.BitmapSource> ekvivalentní a se zobrazí jako vstup <xref:System.Windows.Media.Effects.BitmapEffect>. Nahradí výstup <xref:System.Windows.Media.Visual> výchozí chování vykreslování objektu. To je důvod, proč <xref:System.Windows.Media.Effects.BitmapEffect> objekty vynutit vizuály k vykreslení v softwaru pouze to znamená bez hardwarovou akceleraci ve vizuálech při použití účinky.  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> simuluje objekt, který se zobrazí na více instancí fokus.  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> Vytvoří Haló barvy kolem objektu.  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> vytvoří stín za objektem.  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> Vytvoří zkosení, což vyvolá na plochu bitovou kopii podle zadaná křivka.  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> vytvoří mapování hrbolů <xref:System.Windows.Media.Visual> poskytnout dojem hloubky a textury z umělé zdroji světla.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bitmapové efekty jsou vykreslovány v režimu software. Libovolný objekt, který se použije efekt zobrazí také v softwaru. Nejvíce při použití rastrový obrázek účinky na velké vizuály nebo animování vlastnosti efektu rastrového obrázku má snížený výkon. To je Řekněme, že tímto způsobem vůbec neměli používat bitmapových efektů, že by měl buďte opatrní a důkladně testování pro zajištění, že vaši uživatelé získávají prostředí, které očekáváte.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Bitmapové efekty nepodporují spouštění v částečném vztahu důvěryhodnosti. Aplikace musí mít oprávnění úplný vztah důvěryhodnosti bitmapových efektů.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Postup použití efektu  
 <xref:System.Windows.Media.Effects.BitmapEffect> je vlastnost na <xref:System.Windows.Media.Visual>. Proto použití efektů Vizuály, například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>, nebo <xref:System.Windows.UIElement>, je stejně jednoduché jako nastavení vlastnosti. <xref:System.Windows.UIElement.BitmapEffect%2A> můžete nastavit na jediné <xref:System.Windows.Media.Effects.BitmapEffect> objekt nebo několik efektů možné zřetězit pomocí <xref:System.Windows.Media.Effects.BitmapEffectGroup> objektu.  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Effects.BitmapEffect> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Effects.BitmapEffect> v kódu.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  Když <xref:System.Windows.Media.Effects.BitmapEffect> platí pro kontejner rozložení, jako například <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.Canvas>, účinek se použije pro vizuální strom elementu nebo vizuál, včetně všech jeho podřízených elementů.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Vytvoření vlastních efektů  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] také poskytuje nespravovaná rozhraní k vytvoření vlastních efektů, které lze použít ve spravované [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací. Další referenční materiál pro vytvoření vlastní bitmapových efektů, naleznete v tématu [nespravované WPF rastrový efekt](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) dokumentaci.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [Bitmapový efekt nespravované WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)  
 [Přehled obrázků](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Zabezpečení](../../../../docs/framework/wpf/security-wpf.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
