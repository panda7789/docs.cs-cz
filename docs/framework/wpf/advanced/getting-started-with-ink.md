---
title: "Začínáme s inkoustem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c977e8a4a23f9739541cf28d9e34ad9e8db1daf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-ink"></a>Začínáme s inkoustem
Zařadit digitálního do svých aplikací je jednodušší než kdy dřív. Element Ink byla vyvinuta ze se nezbytným důsledkem metodu COM a systém Windows Forms programování k dosažení úplné integrace do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Není nutné k instalaci modulu runtime knihovny nebo samostatné sady SDK.  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete použít v následujících příkladech, je nutné nejprve nainstalovat Microsoft Visual Studio 2005 a [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Musíte taky vědět, jak pro psaní aplikací pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Další informace o začátcích se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="quick-start"></a>Rychlý Start  
 Tato část vám pomůže psát jednoduché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, která shromažďuje rukopisu.  
  
 Pokud jste tak již neučinili, nainstalujte Microsoft Visual Studio 2005 a [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace obvykle musí být zkompilovány, abyste mohli zobrazit i v případě, že se skládat pouze z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Ale [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] zahrnuje aplikace, aplikaci XamlPad, navržená tak, aby proces implementace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]– na základě uživatelského rozhraní. Tuto aplikaci můžete použít k zobrazení a pustíte do optimalizace s první několik ukázky v tomto dokumentu. Proces vytváření kompilované aplikace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je popsané dál v tomto dokumentu.  
  
 Chcete-li spustit aplikaci XAMLPad, klikněte na tlačítko **spustit** nabídky, přejděte na příkaz **všechny programy**, přejděte na **Microsoft Winndows SDK**, přejděte na příkaz **nástroje**a klikněte na tlačítko **Aplikaci XAMLPad**. V podokně vykreslování vykreslí aplikaci XAMLPad XAML kód napsaný v podokně kódu. Můžete upravit kód XAML a změny se okamžitě zobrazí v podokně vykreslování.  
  
#### <a name="got-ink"></a>Máte rukopisu?  
 Spuštění prvního [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, která podporuje rukopisu:  
  
1.  Otevřete sadu Microsoft Visual Studio 2005  
  
2.  Vytvořte novou **aplikace WPF (Windows)**  
  
3.  Typ `<InkCanvas/>` mezi `<Grid>` značky  
  
4.  Stiskněte klávesu **F5** ke spuštění aplikace v ladicím programu  
  
5.  Pomocí pera nebo myš, zápis **hello, world** v okně  
  
 Napsání ekvivalentní rukopisu "hello, world" aplikace s pouze 12 stisknutí kláves!  
  
#### <a name="spice-up-your-application"></a>Okořeňte do vaší aplikace  
 Umožňuje využít výhod některé funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Nahraďte všechno mezi otevření \<okno > a zavření \</Window > značky s následující kód k získání štětce přechodu pozadí na vaší ploše rukopisu.  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a>Pomocí animace  
 Cvičně si můžeme animace barvy štětce přechodu. Přidejte následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] po zavření `</InkCanvas>` značky, ale před uzavírací `</Page>` značky.  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a>Přidání některé kódu XAML  
 Při XAML lze velmi snadno návrh uživatelského rozhraní, musí všechny reálné aplikaci přidat kód pro zpracování událostí. Zde je jednoduchý příklad, který zvětší rukopisu v reakci na klikněte pravým tlačítkem myši:  
  
 Nastavte `MouseRightButtonUp` obslužné rutiny ve vaší [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 V Průzkumníku řešení v sadě Visual Studio rozbalte Windows1.xaml a otevřete soubor modelu code-behind, Window1.xaml.cs nebo Window1.xaml.vb, pokud používáte Visual Basic. Přidejte následující kód obslužné rutiny událostí:  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 Nyní spusťte aplikaci. Přidat rukopisu a pak klikněte pravým tlačítkem myši nebo provést ekvivalent stiskněte a podržte pomocí pera.  
  
#### <a name="using-procedural-code-instead-of-xaml"></a>Použití procedurální kódu místo XAML  
 Můžete přístup k veškerým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce z procedurální kódu. Tady je "Hello rukopisu World" aplikaci pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , nepoužívá žádné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vůbec. Vložte kód pod do prázdné aplikace konzoly v sadě Visual Studio. Přidejte odkazy na sestavení PresentationCore PresentationFramework a WindowsBase a sestavte aplikaci stisknutím **F5**:  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Rukopis](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [Shromáždění rukopisu](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [Rozpoznávání textu psaného rukou](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [Uložení rukopisu](../../../../docs/framework/wpf/advanced/storing-ink.md)
