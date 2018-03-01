---
title: "Přehled efektů bitmap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f642c699a0ecf3e3cce328363f90110766002e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="bitmap-effects-overview"></a>Přehled efektů bitmap
Rastrový obrázek důsledky povolit návrháře a vývojáře vizuálních efektů použít k vykreslení [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] obsah. Například rastrový obrázek důsledky umožňují snadno aplikovat <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> vliv nebo efekt rozostření bitovou kopii nebo tlačítko.  
  
> [!IMPORTANT]
>  V [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] nebo novější, <xref:System.Windows.Media.Effects.BitmapEffect> třída je zastaralá. Pokud se pokusíte použít <xref:System.Windows.Media.Effects.BitmapEffect> třída, zobrazí se výjimku zastaralé. Aktuální alternativa k <xref:System.Windows.Media.Effects.BitmapEffect> třída je <xref:System.Windows.Media.Effects.Effect> třídy. Ve většině případů <xref:System.Windows.Media.Effects.Effect> třída je výrazně rychlejší.  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Účinky rastrový obrázek WPF  
 Rastrové efekty (<xref:System.Windows.Media.Effects.BitmapEffect> objektu) jsou jednoduché pixelů operace zpracování. Efekt rastrového obrázku trvá <xref:System.Windows.Media.Imaging.BitmapSource> jako vstup a vytváří nový <xref:System.Windows.Media.Imaging.BitmapSource> po použití platit, jako je například rozostření nebo vyřaďte stínové. Každý efekt rastrového obrázku zpřístupní vlastnosti, které můžete řídit filtrování vlastností, jako například <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> z <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Ve speciálním případě v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], důsledky lze nastavit jako vlastnosti v za provozu <xref:System.Windows.Media.Visual> objekty, například <xref:System.Windows.Controls.Button> nebo <xref:System.Windows.Controls.TextBox>. Zpracování pixelů je použít a vykreslit za běhu. V takovém případě při vykreslování <xref:System.Windows.Media.Visual> je automaticky převeden na jeho <xref:System.Windows.Media.Imaging.BitmapSource> ekvivalentní a předány jako vstup <xref:System.Windows.Media.Effects.BitmapEffect>. Nahradí výstup <xref:System.Windows.Media.Visual> objektu Výchozí vykreslování chování. To je důvod, proč <xref:System.Windows.Media.Effects.BitmapEffect> objekty vynutit vizuály k vykreslení v softwaru pouze tj žádné hardwarovou akceleraci vizuálů, kdy se mají použít účinky.  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect>simuluje objekt, který se zobrazí se na fokus.  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>Vytvoří bylo barvy kolem objektu.  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>vytvoří stín za objekt.  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect>Vytvoří zkosení, což zvyšuje prostor bitovou kopii podle zadaného křivky.  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect>Vytvoří hrbolů mapování <xref:System.Windows.Media.Visual> budit dojem hloubky a texture z umělé zdroje světla.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]účinky rastrového obrázku jsou vykreslovány v režimu softwaru. Libovolný objekt, který se vztahuje vliv budou také vykresleny v softwaru. Je ke snížení výkonu nejvíce při použití rastrový obrázek dopad na velké vizuály nebo animování vlastnosti Efekt rastrového obrázku. Toto je nechcete Řekněme, že byste neměli používat rastrový obrázek důsledky tímto způsobem na všechny, ale měli buďte opatrní a důkladně otestovat zajistit, že jsou vaši uživatelé získávání zkušeností, které očekáváte, že.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]rastrový obrázek důsledky nepodporují spouštění částečnou důvěryhodností. Aplikace musí mít úplná oprávnění pro použití důsledky rastrového obrázku.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Jak se má použít efekt  
 <xref:System.Windows.Media.Effects.BitmapEffect>je vlastnost na <xref:System.Windows.Media.Visual>. Proto použití důsledky vizuální prvky, jako například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>, nebo <xref:System.Windows.UIElement>, je stejně snadná jako nastavení vlastnosti. <xref:System.Windows.UIElement.BitmapEffect%2A>můžete nastavit na jednu <xref:System.Windows.Media.Effects.BitmapEffect> objektu nebo několika důsledky možné zřetězit pomocí <xref:System.Windows.Media.Effects.BitmapEffectGroup> objektu.  
  
 Následující příklad ukazuje, jak se má použít <xref:System.Windows.Media.Effects.BitmapEffect> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 Následující příklad ukazuje, jak se má použít <xref:System.Windows.Media.Effects.BitmapEffect> v kódu.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  Když <xref:System.Windows.Media.Effects.BitmapEffect> se použije pro kontejner rozložení, jako například <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.Canvas>, účinek se použije pro vizuální strojové struktuře elementu nebo visual, včetně všech jeho podřízených elementů.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Vytváření vlastních efekty  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]také poskytuje nespravovaná rozhraní pro vytvoření vlastní účinky, které lze použít ke správě v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace. Další referenčního materiálu pro vytvoření vlastní rastrový obrázek důsledky, najdete v článku [nespravované efekt rastrového obrázku WPF](https://msdn.microsoft.com/library/ms735092.aspx) dokumentaci.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [Efekt rastrového obrázku nespravované WPF](https://msdn.microsoft.com/library/ms735092.aspx)  
 [Přehled obrázků](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Zabezpečení](../../../../docs/framework/wpf/security-wpf.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
