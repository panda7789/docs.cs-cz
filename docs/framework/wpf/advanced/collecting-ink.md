---
title: "Shromáždění inkoustu"
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
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbf55b5d84420a6aa7af06e94497a85a2b54a0c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-ink"></a>Shromáždění inkoustu
[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platformy shromažďuje digitální rukopisu v rámci základní ze svých funkcí. Toto téma popisuje metody pro kolekci ručně vytvořených objektů v [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete použít v následujících příkladech, je nutné nejprve nainstalovat [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] a [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Musíte taky vědět, jak pro psaní aplikací pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Další informace o začátcích se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="using-the-inkcanvas-element"></a>Pomocí elementu InkCanvas  
 <xref:System.Windows.Controls.InkCanvas> Element poskytuje nejjednodušší způsob, jak shromažďovat rukopisu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.InkCanvas> Element je podobná [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) objektu z [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] a starší verze.  
  
 Použijte <xref:System.Windows.Controls.InkCanvas> elementu, který chcete přijímat a zobrazovat vstup rukopisu. Můžete vložit běžně rukopisu pomocí pera, která komunikuje s digitizéru k vytvoření tahy. Kromě toho myši jde použít místo pera. Vytvořený tahy jsou reprezentovány jako <xref:System.Windows.Ink.Stroke> objekty a jejich smí uživatel manipulovat prostřednictvím kódu programu i uživatelem vstup. <xref:System.Windows.Controls.InkCanvas> Umožňuje uživatelům vybrat, upravit nebo odstranit existující <xref:System.Windows.Ink.Stroke>.  
  
 S použitím jazyka XAML, můžete nastavit rozpoznávání rukopisu snadno jako přidání `InkCanvas` element vašeho stromu. Následující příklad přidá <xref:System.Windows.Controls.InkCanvas> k výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvořených v projektů [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 `InkCanvas` Element může obsahovat také podřízené elementy, které umožňují přidání možností poznámky rukopisu na téměř jakoukoli typ elementu XAML. Zkontrolujte například, pro přidání možností rukopisu do textový element, jednoduše ho podřízenou <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 Přidání podpory pro vytváření bitové kopie pomocí rukopisu poznámek je stejně jednoduché.  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a>Režimy InkCollection  
 <xref:System.Windows.Controls.InkCanvas> Poskytuje podporu pro různé vstupní způsoby pomocí jeho <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> vlastnost.  
  
### <a name="manipulating-ink"></a>Manipulace s rukopisu  
 <xref:System.Windows.Controls.InkCanvas> Poskytuje podporu pro mnoho ink úpravy operace. Například <xref:System.Windows.Controls.InkCanvas> podporuje back z – pera vymazat s žádný další kód potřebné k přidání funkce do elementu.  
  
#### <a name="selection"></a>Výběr  
 Nastavení režimu výběru je jednoduché, nastavení <xref:System.Windows.Controls.InkCanvasEditingMode> vlastnost **vyberte**. Následující kód nastaví režimu úprav, které jsou založené na hodnotu <xref:System.Windows.Forms.CheckBox>:  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a>DrawingAttributes  
 Použití <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> vlastnost změnit vzhled tahy. Například <xref:System.Windows.Ink.DrawingAttributes.Color%2A> členem <xref:System.Windows.Ink.DrawingAttributes> nastaví barvu vygenerované <xref:System.Windows.Ink.Stroke>. Následující příklad změní na červenou barvu vybrané tahy.  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Vlastnost poskytuje přístup k vlastnosti, například výška, šířku a barvu tahy vytvořené v <xref:System.Windows.Controls.InkCanvas>. Jakmile změníte <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, všechny budoucí tahy vloženy do <xref:System.Windows.Controls.InkCanvas> se vykreslují nové hodnoty vlastností.  
  
 Kromě úpravy <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> v souboru kódu na pozadí, můžete pomocí syntaxe jazyka XAML pro zadání <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnosti. Následující kód XAML ukazuje, jak nastavit <xref:System.Windows.Ink.DrawingAttributes.Color%2A> vlastnost. Pokud chcete použít tento kód, vytvořte novou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt s názvem "HelloInkCanvas" v sadě Visual Studio 2005. Nahraďte kód v souboru Window1.xaml následujícím kódem.  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 V dalším kroku přidejte následující obslužné rutiny událostí tlačítko do souboru ve třídě Window1 kódu.  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 Po zkopírování tento kód, stiskněte klávesu **F5** sady Microsoft Visual Studio 2005 ke spuštění programu v ladicím programu.  
  
 Všimněte si jak <xref:System.Windows.Controls.StackPanel> umístí tlačítka na <xref:System.Windows.Controls.InkCanvas>. Pokud se pokusíte rukopisu v horní části tlačítka, <xref:System.Windows.Controls.InkCanvas> shromažďuje a vykreslí element ink za tlačítka. Důvodem je, že tlačítka jsou obsahující členy stejné úrovně <xref:System.Windows.Controls.InkCanvas> a podřízené objekty. Tlačítka jsou také vyšší v pořadí, takže rukopisu vykreslením za je.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
