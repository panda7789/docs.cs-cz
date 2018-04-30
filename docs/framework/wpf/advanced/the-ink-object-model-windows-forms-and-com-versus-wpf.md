---
title: 'Model inkoustových objektů: Windows Forms a COM vzhledem k platformě WPF'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 06a2c2049ec7fe7046bd6dae2711fe8e46592fcf
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Model inkoustových objektů: Windows Forms a COM vzhledem k platformě WPF

Jsou v podstatě tři platformách, které podporují digitální rukopisu: platformy Tablet PC Windows Forms, Tablet PC COM platformy a platformy Windows Presentation Foundation (WPF).  Windows Forms a COM platformy sdílení, podobně jako objekt modelu, ale objekt modelu pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformy se podstatně liší.  Toto téma popisuje rozdíly v hlavní tak, aby vývojáři, kteří již dříve pracovali s modelem jeden objekt může lépe pochopit dalších.  
  
## <a name="enabling-ink-in-an-application"></a>Povolení rukopisu v aplikaci  
 Všechny tři platformy dodávat objekty a ovládací prvky, které povolit aplikaci přijímat vstup z pera.  Windows Forms a platformy COM dodávají spolu s [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) a [ Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) třídy.  [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) a [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx) jsou ovládací prvky, které můžete přidat aplikace do shromažďovat rukopisu.  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) a [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) se dá připojit ke stávajícím okně rukopisu enable windows a vlastní ovládací prvky.  
  
 Platforma WPF obsahuje <xref:System.Windows.Controls.InkCanvas> ovládacího prvku.  Můžete přidat <xref:System.Windows.Controls.InkCanvas> do vaší aplikace a spustíte shromažďování rukopisu okamžitě. Pomocí <xref:System.Windows.Controls.InkCanvas>, může uživatel kopírovat, vyberte a změna velikosti rukopisu.  Můžete přidat další ovládací prvky na <xref:System.Windows.Controls.InkCanvas>, a uživatele můžete psát rukou prostřednictvím těchto ovládacích prvků, příliš.  Můžete vytvořit vlastní ovládací prvek povoleno rukopisu přidáním <xref:System.Windows.Controls.InkPresenter> a shromažďování jeho pera body.  
  
 Následující tabulka uvádí, kde má být další informace o povolení rukopisu v aplikaci:  
  
|K tomu...|Na platformě WPF...|Na platformách Windows Forms nebo COM...|  
|-----------------|--------------------------|------------------------------------------|  
|Přidání ovládacího prvku rukopisu do aplikace|V tématu [Začínáme s rukopisu](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).|V tématu [deklarace identity pro automatické vytvoření vzorku](http://msdn.microsoft.com/bec4333a-62ca-4254-a39b-04bc2c556992)|  
|Povolit rukopisu ve vlastní ovládací prvek|V tématu [vytváření rukou vstupní ovládací prvek](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).|V tématu [Ink schránky ukázka](http://msdn.microsoft.com/a0c42f1c-543d-44f8-83d9-fe810de410ff).|  
  
## <a name="ink-data"></a>Element Ink dat  
 Windows Forms a platformy COM [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), a [ Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) každý zveřejněte [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objektu. [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objektu obsahuje data pro jeden nebo více [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objekty a zveřejňuje běžné metody a vlastnosti, které chcete spravovat a zpracování těchto tahy.  [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objekt spravuje životnost tahy obsahuje; [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objekt vytvoří nebo odstraní tahy, které je vlastní.  Každý [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx) má identifikátor, který je jedinečná v rámci nadřazené [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objektu.  
  
 Na platformě WPF <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> třída vlastní a spravuje vlastní životního cyklu. Skupina <xref:System.Windows.Ink.Stroke> objekty může být seskupeny v <xref:System.Windows.Ink.StrokeCollection>, který poskytuje metody pro barvu, běžné operace správy dat, jako dosáhl testování, aktualizovat je, vymazat, transformace a serializaci rukopisu. A <xref:System.Windows.Ink.Stroke> můžou patřit do nula, jednu nebo více <xref:System.Windows.Ink.StrokeCollection> objekty kdykoli dává času.  Místo nutnosti [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objekt, <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter> obsahovat <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 Následující ilustrace dvojice porovná objektové modely dat rukopisu.  Windows Forms a COM platformy [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objekt omezí životnost [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objekty a pera pakety patří do jednotlivých tahy.  Dvě nebo více tahy může odkazovat stejné [Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType) objektu, jak je znázorněno na následujícím obrázku.  
  
 ![Diagram objektového modelu rukopisu pro model COM&#47;Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], každý <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> je common language runtime objekt, který existuje tak dlouho, dokud něco obsahuje odkaz na jeho.  Každý <xref:System.Windows.Ink.Stroke> odkazy <xref:System.Windows.Input.StylusPointCollection> a <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> objektu, která jsou také běžně používané objekty runtime jazyka.  
  
 ![Diagram objektového modelu rukopisu pro grafický subsystém WPF. ] (../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 Následující tabulka porovnává jak provést některé běžné úlohy na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformy Windows Forms a rozhraní COM a platformu.  
  
|Úloha|Windows Presentation Foundation|Windows Forms a modelu COM|  
|----------|-------------------------------------|---------------------------|  
|Uložit rukopisu|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))|  
|Element Ink zatížení|Vytvoření <xref:System.Windows.Ink.StrokeCollection> s <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> konstruktor.|[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)|  
|Stiskněte tlačítko test|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://msdn.microsoft.com/library/aa515934.aspx)|  
|Zkopírujte rukopisu|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)|  
|Vložení rukopisu|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)|  
|Přístup na kolekci tahy vlastní vlastnosti|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (vlastnosti jsou uloženy interně a přístupných přes <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>, a <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|Použití [Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)|  
  
### <a name="sharing-ink-between-platforms"></a>Sdílení rukopisu mezi platformami  
 I když platformy mají různé objektové modely pro data rukopisu, sdílení dat mezi platformy je velmi snadné. Následující příklady uložte rukopisu z aplikace Windows Forms a načtení rukopisu do aplikace Windows Presentation Foundation.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Následující příklady uložte rukopisu z aplikace Windows Presentation Foundation a načtení rukopisu do aplikace Windows Forms.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Události z pera  
 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), a [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) na Windows Forms a COM platformy přijímat události při uživatele vstupy pera data.  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) nebo [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) je připojena k okno nebo ovládacího prvku a se mohou přihlásit k události vyvolané službou tablet vstupní data.  Vlákno, kdy dojde k těmto událostem závisí na tom, jestli jsou vyvolány události s pera, myši, nebo prostřednictvím kódu programu.  Další informace o vláken ve vztahu k těmto událostem najdete v tématu [Obecné aspekty dělení na vlákna](http://msdn.microsoft.com/cf35724f-5f80-4b3e-992a-a9d5ea99aae9) a [vláken, na které můžete aktivovat událost](http://msdn.microsoft.com/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f).  
  
 Na platformě Windows Presentation Foundation <xref:System.Windows.UIElement> třída má události pro vstup pomocí pera. To znamená, že každý prvek poskytuje úplnou sadu událostí pera.  Událostí pera mít tunelování šíření událost páry a vždy odehrávat na vlákno aplikace.  Další informace najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Následující diagram ukazuje porovná objektové modely pro třídy, které vyvolávání událostí pera. Objektový model Windows Presentation Foundation zobrazuje pouze probublávání události, není tunelu protějšky událostí.  
  
 ![Diagram událostí pera v grafickém subsystému WPF a Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Data pera  
 Všechny tři platformy poskytují způsoby, jak zachytit a pracovat s daty, která se dodává z pera.  Ve Windows Forms a platformy COM, to je dosaženo vytvořením [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx), okno nebo ovládací prvek se připojuje k němu a vytváření třídy, která implementuje [ Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx) nebo [Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx) rozhraní. Vlastní modul plug-in se pak přidá do modulu plug-in kolekce [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx). Další informace o tomto objektu modelu najdete v tématu [Architektura rozhraní API StylusInput](http://msdn.microsoft.com/88bab0ab-df9f-4813-9a9f-9a137813f0b4).  
  
 Na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformy, <xref:System.Windows.UIElement> třída poskytuje kolekci moduly plug-in, podobně jako v návrhu, které [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).  Zachytávat data pera, vytvořte třídu, která dědí z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a přidejte objekt, který má <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce <xref:System.Windows.UIElement>. Další informace o tato interakce najdete v tématu [brání vstup z pera](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md).  
  
 Na všech platformách fondu vláken přijímá data rukopisu prostřednictvím událostí pera a odešle ji do aplikace vlákno.  Další informace o dělení na vlákna na COM a platformy systému Windows najdete v tématu [dělení na vlákna důležité informace týkající se rozhraní API StylusInput](http://msdn.microsoft.com/5d98768a-c60b-4bb0-8640-9bf38254d41f).  Další informace o dělení na vlákna na prezentační Software Windows najdete v tématu [modelu dělení na vlákna rukopisu](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).  
  
 Na následujícím obrázku porovná objektové modely pro třídy, které získávají data pera na fond pen vláken.  
  
 ![Diagram StylusPlugin modelu WPF vs Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")
