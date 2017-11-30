---
title: "Postupy: Vytvoření textu se stínem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bbc3da54c10304e52f93d38365a8d9ed005505
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-text-with-a-shadow"></a>Postupy: Vytvoření textu se stínem
Příklady v této části ukazují, jak vytvořit efekt stínu pro zobrazený text.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Effects.DropShadowEffect> Objekt umožňuje vytvořit stínové důsledky pro celou řadu rozevírací [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objekty. Následující příklad ukazuje efekt stínu rozevírací použít na text. V takovém případě stínové kopie je logicky shadow, což znamená rozostření barvu stínu.  
  
 ![Stín textu zobrazovat s Měkkost & č. 61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Příklad textu logicky stínové  
  
 Můžete řídit šířku stínu nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> vlastnost. Hodnota `4.0` Určuje šířku stínové 4 pixelů. Můžete řídit Měkkost, nebo rozostření stínu změnou <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost. Hodnota `0.0` označuje bez rozostření. Následující příklad kódu ukazuje, jak vytvořit logicky stínové.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Tyto důsledky stínové se nepřenášejí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kanálu vykreslování textu. V důsledku toho ClearType vypnutá při použití těchto důsledcích.  
  
 Následující příklad ukazuje efekt stínu pevný rozevírací použít na text. V takovém případě se bude stín hranice.  
  
 ![Stín textu zobrazovat s Měkkost & č. 61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")  
Příklad textu pevný stínové  
  
 Můžete vytvořit pevný stínové nastavením <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> vlastnost `0.0`, což naznačuje, že se používá bez rozostření. Směr stínu, můžete řídit úpravou <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> vlastnost. Nastavte směrovou hodnotu této vlastnosti na určitý stupeň mezi `0` a `360`. Následující obrázek znázorňuje směrovou hodnoty <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> nastavení vlastnosti.  
  
 ![Nastavení stupně DropShadow stínu](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
Směr DropShadow diagram  
  
 Následující příklad kódu ukazuje, jak vytvořit pevný stínové.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Pomocí efekt rozostření  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> slouží k vytvoření efekt stínové jako, který se může za objekt textu. Efekt rozostření rastrový obrázek použít na text rozostří text rovnoměrně ve všech pokynů.  
  
 Následující příklad ukazuje efekt rozostření použít na text.  
  
 ![Stín textu zobrazovat pomocí BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Příklad textu efekt rozostření  
  
 Následující příklad kódu ukazuje, jak vytvořit efekt rozostření.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Pomocí přeložit transformace  
 A <xref:System.Windows.Media.TranslateTransform> slouží k vytvoření efekt stínové jako, který se může za objekt textu.  
  
 Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunutí textu. V tomto příkladu se vytvoří kopii text pod primární text mírně posunutí efekt stínu.  
  
 ![Stín textu zobrazovat pomocí TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")  
Příklad použití transformace pro přidání stínu textu  
  
 Následující příklad kódu ukazuje, jak vytvořit transformace pro přidání stínu.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
