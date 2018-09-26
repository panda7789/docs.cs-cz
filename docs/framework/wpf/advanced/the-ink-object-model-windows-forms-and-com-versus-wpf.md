---
title: 'Model inkoustových objektů: Windows Forms a COM vzhledem k platformě WPF'
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
ms.openlocfilehash: c351f3d6bf6dbaf94d865fd56e140c44edc20394
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231505"
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Model inkoustových objektů: Windows Forms a COM vzhledem k platformě WPF

Jsou v podstatě třech platformách, které podporují digitálních inkoust: platforma Tablet PC Windows Forms, Tablet PC COM platformu a platformu Windows Presentation Foundation (WPF).  Windows Forms a COM platformy sdílené složky podobně jako objekt modelu, ale objekt model pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformy se podstatně liší.  Toto téma popisuje rozdíly v hlavní tak, aby vývojáři, kteří pracovali s jedním objektem modelu můžete lépe pochopili druhé.  
  
## <a name="enabling-ink-in-an-application"></a>Povolení inkoustu v aplikaci  
 Všechny tři platformy dodávat objektů a ovládacích prvků, které umožňují aplikacím přijímat vstupu z pera.  Windows Forms a COM platformy dodávají spolu s [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) a [ Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) třídy.  [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) a [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx) jsou ovládací prvky, které můžete přidat k aplikaci ke shromáždění rukopisu.  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) a [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) lze připojit k existujícímu oknu windows ink povolit a vlastních ovládacích prvků.  
  
 Zahrnuje platformu WPF <xref:System.Windows.Controls.InkCanvas> ovládacího prvku.  Můžete přidat <xref:System.Windows.Controls.InkCanvas> pro vaši aplikaci a začněte shromažďovat inkoustu okamžitě. S <xref:System.Windows.Controls.InkCanvas>, uživatel můžete zkopírovat, vyberte a změna velikosti rukopisu.  Můžete přidat další ovládací prvky na <xref:System.Windows.Controls.InkCanvas>, a uživatel může příliš psaní přes tyto ovládací prvky.  Můžete vytvořit vlastní ovládací prvek inkoustu povolené tak, že přidáte <xref:System.Windows.Controls.InkPresenter> a shromažďování svých bodů stylus.  
  
 Následující tabulka uvádí, kde získat další informace o povolení inkoustu v aplikaci:  
  
|Provedete to tak...|Na platformě WPF...|Na platformách Windows Forms a COM...|  
|-----------------|--------------------------|------------------------------------------|  
|Přidat do aplikace ovládací prvek inkoustu|Zobrazit [Začínáme s rukopisem](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).|Zobrazit [deklarací identity pro automatické vytvoření vzorku](/windows/desktop/tablet/auto-claims-form-sample)|  
|Povolení inkoustu na vlastním ovládacím prvku|Zobrazit [vytváření rukou vstupní ovládací prvek](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).|Zobrazit [inkoustu schránky ukázka](/windows/desktop/tablet/ink-clipboard-sample).|  
  
## <a name="ink-data"></a>Data inkoustu  
 Ve Windows Forms a COM platformy [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), a [ Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) každý vystavení [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objektu. [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objekt obsahuje data pro jeden nebo více [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objektů a poskytuje běžné metody a vlastnosti, které chcete spravovat a manipulovat s těmito tahů.  [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objekt spravuje životnost tahy obsahuje; [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objekt vytvoří a odstraní tahy, které vlastní.  Každý [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx) má identifikátor, který je jedinečný v rámci svého nadřazeného objektu [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objektu.  
  
 Na platformě WPF <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> třídy vlastní a spravuje svou vlastní životnost. Skupina <xref:System.Windows.Ink.Stroke> objekty můžou shromažďovat společně v <xref:System.Windows.Ink.StrokeCollection>, který poskytuje metody pro běžné inkoustu operací správy dat, jako testování, mazání, transformace a serializaci rukopis přístupů. A <xref:System.Windows.Ink.Stroke> může patřit k žádným, jedním nebo více <xref:System.Windows.Ink.StrokeCollection> objekty na libovolné dali čas.  Namísto toho, aby [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objektu, <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter> obsahovat <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 Následující pár ilustrace porovnává objektové modely dat rukopisu.  Ve Windows Forms a COM platformy [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) omezuje životnost objektu [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objekty a stylus pakety patří do jednotlivých tahů.  Dva nebo více tahy může odkazovat na stejný [Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType) objektu, jak je znázorněno na následujícím obrázku.  
  
 ![Diagram Model inkoustových objektů modelu COM&#47;Winforms. ](../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]každá <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> je common language runtime objekt, který existuje za předpokladu, něco se na ni odkaz.  Každý <xref:System.Windows.Ink.Stroke> odkazy <xref:System.Windows.Input.StylusPointCollection> a <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> objektu, které jsou také běžně používané objekty modulu runtime jazyka.  
  
 ![Diagram Model inkoustových objektů pro WPF. ](../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 Následující tabulka porovnává tom, jak provádět několik běžných úloh na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformu a platformy Windows Forms a COM.  
  
|Úloha|Windows Presentation Foundation|Windows Forms a COM|  
|----------|-------------------------------------|---------------------------|  
|Uložení inkoustu|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))|  
|Načtení inkoustu|Vytvoření <xref:System.Windows.Ink.StrokeCollection> s <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> konstruktoru.|[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)|  
|Spuštění testu|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://msdn.microsoft.com/library/aa515934.aspx)|  
|Zkopírujte inkoustu|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)|  
|Vložte inkoustu|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)|  
|Přístup k vlastní vlastnosti v kolekci tahy|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (vlastnosti jsou uloženy interně a získávat přístup k <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>, a <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|Použití [Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)|  
  
### <a name="sharing-ink-between-platforms"></a>Sdílení mezi platformami inkoustu  
 I když platformy mají různé objektové modely dat rukopisu, sdílení dat mezi platformy je velmi snadné. Následující příklady uložení rukopisu z aplikace Windows Forms a načtení inkoustu do aplikace Windows Presentation Foundation.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Následující příklady uložení rukopisu z aplikace Windows Presentation Foundation a načtení inkoustu do aplikace Windows Forms.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Události z pera  
 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), a [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) ve Windows Forms a COM platformy příjem událostí při uživatele vstupy pera data.  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) nebo [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) je připojena k okno nebo ovládacího prvku a události vyvolané službou vstupní data tabletu můžete odebírat.  Vlákno, na kterém dojde k těmto událostem závisí na tom, jestli události jsou vyvolány pomocí pera, myši, nebo prostřednictvím kódu programu.  Další informace o dělení na vlákna ve vztahu k těmto událostem v tématu [Obecné aspekty práce s vlákny](/windows/desktop/tablet/general-threading-considerations) a [vlákna událost může aktivovat](/windows/desktop/tablet/threads-on-which-an-event-can-fire).  
  
 Na platformě Windows Presentation Foundation <xref:System.Windows.UIElement> třída obsahuje události pro vstup pomocí pera. To znamená, že každý ovládací prvek poskytuje úplnou sadu událostí pera.  Události stylus mají šíření a tunelové propojení událostí dvojice a vždy odehrávat na vlákna aplikace.  Další informace najdete v tématu [směrovat Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Následující diagram porovnává objektové modely tříd, které vyvolávají události stylus. Objektový model Windows Presentation Foundation zobrazí pouze šíření událostí, ne tunelového propojení událost protějšky.  
  
 ![Diagram Stylus událostí v subsystému WPF a Winforms. ](../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Data pera  
 Všechny tři platformy poskytují způsoby, jak zachytit a manipulaci s daty, která pocházejí z pera.  Ve Windows Forms a COM platformy, tím se dosahuje vytvořením [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx)připojení ovládacího prvku okno nebo k němu a vytvoření třídy, která implementuje [ Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx) nebo [Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx) rozhraní. Vlastní modul plug-in se pak přidá do modulu plug-in kolekce [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx). Další informace o tomto objektu modelu, naleznete v tématu [Architektura rozhraní API StylusInput](/windows/desktop/tablet/architecture-of-the-stylusinput-apis).  
  
 Na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformy, <xref:System.Windows.UIElement> třída zveřejňuje sadu modulů plug-in, podobně jako v návrhu tak, aby [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).  Aby se zachytily pera, vytvořte třídu, která dědí z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a přidejte objekt, který má <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce <xref:System.Windows.UIElement>. Další informace o interakci najdete v tématu [přijetí vstupu z pera](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md).  
  
 Na všech platformách fondu vláken přijímá data inkoustu prostřednictvím stylus událostí a odesílá je do vlákna aplikace.  Další informace o dělení na vlákna v modelu COM a platformách Windows, naleznete v tématu [dělení na vlákna důležité informace týkající se rozhraní API StylusInput](/windows/desktop/tablet/threading-considerations-for-the-stylusinput-apis).  Další informace o vláknech na prezentační Software Windows najdete v tématu [The Model vláken inkoustu](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).  
  
 Následující obrázek porovnává objektové modely pro třídy, které získávají data pera ve fondu vláken pera.  
  
 ![Diagram StylusPlugin – model WPF a Winforms. ](../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")
