---
title: Digitální inkoust – model Windows Forms a COM vs. WPF
titleSuffix: ''
ms.date: 03/30/2017
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
ms.openlocfilehash: 4a183bba2c5cfb2d12a9cf435ae1f92b4cf63948
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737295"
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Model inkoustových objektů: Windows Forms a COM vzhledem k platformě WPF

K dispozici jsou v podstatě tři platformy, které podporují digitální tisk: počítač s tabletem model Windows Forms platforma, platforma COM počítače Tablet PC a platforma Windows Presentation Foundation (WPF).  Platformy model Windows Forms a COM sdílejí podobný objektový model, ale objektový model pro platformu WPF je podstatně jiný.  Toto téma popisuje rozdíly na vysoké úrovni tak, aby vývojáři, kteří pracovali s jedním objektovým modelem, lépe porozuměli druhému.  
  
## <a name="enabling-ink-in-an-application"></a>Povolení rukopisu v aplikaci  
 Všechny tři platformy dodávají objekty a ovládací prvky, které umožňují aplikaci přijímat vstupy z tabletového pera.  Platformy model Windows Forms a COM jsou dodávány s [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)), [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) a [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) Classes.  [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) a [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)) jsou ovládací prvky, které můžete přidat do aplikace pro shromažďování rukopisu.  [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) a [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) lze připojit k existujícímu oknu, aby bylo možné povolit Windows a vlastní ovládací prvky pro rukopis.  
  
 Platforma WPF obsahuje ovládací prvek <xref:System.Windows.Controls.InkCanvas>.  Do své aplikace můžete přidat <xref:System.Windows.Controls.InkCanvas> a hned začít shromažďovat rukopis. S <xref:System.Windows.Controls.InkCanvas>může uživatel kopírovat, vybírat a měnit velikost inkoustu.  Do <xref:System.Windows.Controls.InkCanvas>můžete přidat další ovládací prvky a uživatel může tyto ovládací prvky také ručně zadat.  Vlastní ovládací prvek s podporou rukopisu můžete vytvořit přidáním <xref:System.Windows.Controls.InkPresenter> a shromažďováním jeho bodů stylusu.  
  
 Následující tabulka uvádí, kde se dozvíte více o povolování rukopisu v aplikaci:  
  
|Postup...|Na platformě WPF...|Na platformách model Windows Forms/COM...|  
|-----------------|--------------------------|------------------------------------------|  
|Přidání ovládacího prvku s povoleným inkoustem do aplikace|Viz [Začínáme s inkoustem](getting-started-with-ink.md).|Viz [Ukázka automatických deklarací identity Form](/windows/desktop/tablet/auto-claims-form-sample)|  
|Povolit rukopis u vlastního ovládacího prvku|Viz [vytvoření ovládacího prvku vstupu rukopisu](creating-an-ink-input-control.md).|Viz [Ukázka schránky rukopisu](/windows/desktop/tablet/ink-clipboard-sample).|  
  
## <a name="ink-data"></a>Inkoustová data  
 Na platformách model Windows Forms a COM [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))a [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) vystaví objekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) . Objekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) obsahuje data jednoho nebo více objektů [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) a zpřístupňuje společné metody a vlastnosti pro správu a manipulaci s nimi.  Objekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) spravuje životnost tahů, které obsahuje; objekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) vytvoří a odstraní tahy, které vlastní.  Každé rozhraní [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) má identifikátor, který je jedinečný v rámci jeho nadřazeného objektu [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) .  
  
 Na platformě WPF třída <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> vlastní a spravuje svou vlastní dobu života. Skupinu objektů <xref:System.Windows.Ink.Stroke> lze shromažďovat společně v <xref:System.Windows.Ink.StrokeCollection>, která poskytuje metody pro běžné operace správy dat pomocí rukopisu, jako jsou například testování přístupů, mazání, transformace a serializace inkoustu. <xref:System.Windows.Ink.Stroke> může patřit k žádnému nebo jednomu <xref:System.Windows.Ink.StrokeCollection>mu objektu v jakémkoli okamžiku.  Místo toho, aby měl objekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) , <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter> obsahovat <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 Následující pár ilustrací porovná modely datových objektů rukopisu.  Na platformách model Windows Forms a COM objekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) omezuje životnost objektů [Microsoft. Ink. vytáhnout](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) a pakety stylusu patří jednotlivým tazích.  Dva nebo více tahů může odkazovat na stejný objekt [Microsoft. Ink. DrawingAttributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583636(v=vs.90)) , jak je znázorněno na následujícím obrázku.  
  
 ![Diagram modelu objektu Ink pro WinForms modelu COM&#47;](./media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]každý <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> je objekt společného jazykového modulu runtime, který existuje, pokud má něco odkaz na něj.  Každý <xref:System.Windows.Ink.Stroke> odkazuje na objekt <xref:System.Windows.Input.StylusPointCollection> a <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType>, které jsou také objekty společného jazykového modulu runtime.  
  
 ![Diagram objektového modelu rukopisu pro WPF](./media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 Následující tabulka porovnává, jak provést některé běžné úkoly na platformě WPF a na platformách model Windows Forms a COM.  
  
|Úkol|Windows Presentation Foundation|model Windows Forms a COM|  
|----------|-------------------------------------|---------------------------|  
|Uložit rukopis|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft. Ink. Ink. Save](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571335(v=vs.90))|  
|Načíst rukopis|Vytvořte <xref:System.Windows.Ink.StrokeCollection> pomocí konstruktoru <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A>.|[Microsoft. Ink. Ink. Load](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms569609(v=vs.90))|  
|Test volání|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft. Ink. Ink. HitTest](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571330(v=vs.90))|  
|Kopírovat rukopis|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft. Ink. Ink. ClipboardCopy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571316(v=vs.90))|  
|Vložit rukopis|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft. Ink. Ink. ClipboardPaste](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571318(v=vs.90))|  
|Přístup k vlastním vlastnostem pro kolekci tahů|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (vlastnosti se ukládají interně a jsou dostupné přes <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>a <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>).|Použijte [Microsoft. Ink. Ink. ExtendedProperties](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms582214(v=vs.90))|  
  
### <a name="sharing-ink-between-platforms"></a>Sdílení inkoustu mezi platformami  
 I když tyto platformy mají pro data inkoustu odlišné objektové modely, je sdílení dat mezi platformami velmi snadné. Následující příklady uloží rukopis z aplikace model Windows Forms a načtou rukopis do Windows Presentation Foundation aplikace.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Následující příklady uloží rukopis z aplikace Windows Presentation Foundation a načtou rukopis do model Windows Forms aplikace.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Události z tabletového pera  

 Když uživatel zadáte data pera, přijímají se události [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))a [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) na platformách model Windows Forms a com. [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) nebo [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) je připojen k oknu nebo ovládacímu prvku a může se přihlásit k odběru událostí vyvolaných vstupními daty tabletu. Vlákno, ke kterému dojde k těmto událostem, závisí na tom, zda jsou události vyvolány pomocí pera, myši nebo prostřednictvím kódu programu. Další informace o dělení na vlákna ve vztahu k těmto událostem naleznete v tématu [Obecné požadavky na dělení na vlákna](/windows/desktop/tablet/general-threading-considerations) a [vlákna, na kterých může být událost aktivovaná](/windows/desktop/tablet/threads-on-which-an-event-can-fire).  
  
 Na Windows Presentation Foundation platformě mají <xref:System.Windows.UIElement> třídy události pro vstup perem. To znamená, že každý ovládací prvek zveřejňuje úplnou sadu událostí Stylus.  Události tužky mají páry událostí tunelování/probublávání a vždy se vyskytují ve vlákně aplikace.  Další informace najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 Následující diagram znázorňuje porovnání objektových modelů pro třídy, které vyvolávají události stylusu. Objektový model Windows Presentation Foundation zobrazuje pouze události probublávání, nikoli protějšky událostí tunelu.  
  
 ![Diagram událostí stylusu v technologii WPF versus WinForms](./media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Data pera  
 Všechny tři platformy poskytují způsoby, jak zachytit a manipulovat s daty, která se nachází na tabletovém pera.  Na platformách model Windows Forms a COM se to dosáhne vytvořením objektu [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)), připojením okna nebo ovládacího prvku k němu a vytvořením třídy, která implementuje rozhraní [Microsoft. StylusInput. IStylusSyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575201(v=vs.90)) nebo [Microsoft. StylusInput. IStylusAsyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575194(v=vs.90)) . Vlastní modul plug-in se pak přidá do kolekce modulů plug-in modulu [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)). Další informace o tomto objektovém modelu naleznete v tématu [Architektura rozhraní API StylusInput](/windows/desktop/tablet/architecture-of-the-stylusinput-apis).  
  
 Na platformě WPF třída <xref:System.Windows.UIElement> zpřístupňuje kolekci modulů plug-in, podobně jako v návrhu na [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)).  Chcete-li zachytit data pera, vytvořte třídu, která dědí z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a přidejte objekt do kolekce <xref:System.Windows.UIElement.StylusPlugIns%2A> <xref:System.Windows.UIElement>. Další informace o této interakci naleznete v tématu [zachycení vstupu z stylusu](intercepting-input-from-the-stylus.md).  
  
 Na všech platformách fond vláken obdrží data o inkoustu přes události stylusu a pošle je do vlákna aplikace.  Další informace o vláknech na platformách COM a Windows najdete v tématu [požadavky na vlákna pro rozhraní API StylusInput](/windows/desktop/tablet/threading-considerations-for-the-stylusinput-apis).  Další informace o dělení na prezentace v softwaru pro prezentace v systému Windows naleznete v tématu [model vláken inkoustu](the-ink-threading-model.md).  
  
 Následující obrázek porovnává objektové modely pro třídy, které přijímají data pera ve fondu vláken pera.  
  
 ![Diagram modelu StylusPlugin WPF versus WinForms](./media/ink-stylusplugins.png "Ink_StylusPlugins")
