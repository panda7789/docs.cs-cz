---
title: Přehled poznámek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
ms.openlocfilehash: 433fee08d44720640d3f9d1bf2511a6a267eb58e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145459"
---
# <a name="annotations-overview"></a><span data-ttu-id="5d1d6-102">Přehled poznámek</span><span class="sxs-lookup"><span data-stu-id="5d1d6-102">Annotations Overview</span></span>
<span data-ttu-id="5d1d6-103">Psaní poznámek nebo komentářů na papírových dokumentech je tak běžná činnost, že ji téměř považujeme za samozřejmou.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-103">Writing notes or comments on paper documents is such a commonplace activity that we almost take it for granted.</span></span> <span data-ttu-id="5d1d6-104">Tyto poznámky nebo komentáře jsou "poznámky", které přidáme do dokumentu, abychom označili informace nebo zvýraznili položky, které by je zajímaly, pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-104">These notes or comments are "annotations" that we add to a document to flag information or to highlight items of interest for later reference.</span></span> <span data-ttu-id="5d1d6-105">Ačkoli psaní poznámek o tištěných dokumentech je snadné a běžné, schopnost přidávat osobní komentáře k elektronickým dokumentům je obvykle velmi omezená, pokud je vůbec k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-105">Although writing notes on printed documents is easy and commonplace, the ability to add personal comments to electronic documents is typically very limited, if available at all.</span></span>  
  
 <span data-ttu-id="5d1d6-106">Toto téma popisuje několik běžných typů poznámek, konkrétně rychlé poznámky a zvýraznění, a ilustruje, jak rozhraní Microsoft Anotations Framework usnadňuje tyto typy poznámek v aplikacích prostřednictvím nadace Windows Presentation Foundation (WPF ) ovládací prvky pro zobrazení dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-106">This topic reviews several common types of annotations, specifically sticky notes and highlights, and illustrates how the Microsoft Annotations Framework facilitates these types of annotations in applications through the Windows Presentation Foundation (WPF) document viewing controls.</span></span>  <span data-ttu-id="5d1d6-107">WPF ovládací prvky zobrazení dokumentu, <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentScrollViewer>které podporují poznámky patří <xref:System.Windows.Controls.Primitives.DocumentViewerBase> a <xref:System.Windows.Controls.DocumentViewer> <xref:System.Windows.Controls.FlowDocumentPageViewer>, stejně jako ovládací prvky odvozené z například a .</span><span class="sxs-lookup"><span data-stu-id="5d1d6-107">WPF document viewing controls that support annotations include <xref:System.Windows.Controls.FlowDocumentReader> and <xref:System.Windows.Controls.FlowDocumentScrollViewer>, as well as controls derived from <xref:System.Windows.Controls.Primitives.DocumentViewerBase> such as <xref:System.Windows.Controls.DocumentViewer> and <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span></span>  

<a name="caf1_type_stickynotes"></a>
## <a name="sticky-notes"></a><span data-ttu-id="5d1d6-108">Rychlé poznámky</span><span class="sxs-lookup"><span data-stu-id="5d1d6-108">Sticky Notes</span></span>  
 <span data-ttu-id="5d1d6-109">Typická poznámka obsahuje informace napsané na malém kousku barevného papíru, který je pak "přilepená" na dokument.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-109">A typical sticky note contains information written on a small piece of colored paper that is then "stuck" to a document.</span></span> <span data-ttu-id="5d1d6-110">Digitální rychlé poznámky poskytují podobné funkce pro elektronické dokumenty, ale s větší flexibilitou zahrnout mnoho dalších typů obsahu, jako je například zadaný text, ručně psané poznámky (například tablet PC "inkoust" tahy) nebo webové odkazy.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-110">Digital sticky notes provide similar functionality for electronic documents, but with the added flexibility to include many other types of content such as typed text, handwritten notes (for example, Tablet PC "ink" strokes), or Web links.</span></span>  
  
 <span data-ttu-id="5d1d6-111">Následující obrázek znázorňuje některé příklady poznámek poznámky zvýraznění, textové rychlé poznámky a poznámky rychlé poznámky.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-111">The following illustration shows some examples of highlight, text sticky note, and ink sticky note annotations.</span></span>  
  
 <span data-ttu-id="5d1d6-112">![Zvýrazňte poznámky s lepkavou poznámkou pro text a inkoust.](./media/caf-stickynote.jpg "CAF_StickyNote")</span><span class="sxs-lookup"><span data-stu-id="5d1d6-112">![Highlight, text and ink sticky note annotations.](./media/caf-stickynote.jpg "CAF_StickyNote")</span></span>  
  
 <span data-ttu-id="5d1d6-113">Následující příklad ukazuje metodu, kterou můžete použít k povolení podpory poznámky ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-113">The following example shows the method that you can use to enable annotation support in your application.</span></span>  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>
## <a name="highlights"></a><span data-ttu-id="5d1d6-114">Nejzajímavější body</span><span class="sxs-lookup"><span data-stu-id="5d1d6-114">Highlights</span></span>  
 <span data-ttu-id="5d1d6-115">Lidé používají kreativní metody, aby upozornili na zajímavé položky, když označí papírový dokument, jako je podtržení, zvýraznění, kroužení slov ve větě nebo kreslení značek nebo zápisů na okraji.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-115">People use creative methods to draw attention to items of interest when they mark up a paper document, such as underlining, highlighting, circling words in a sentence, or drawing marks or notations in the margin.</span></span>  <span data-ttu-id="5d1d6-116">Zvýraznění poznámek v rozhraní Microsoft Anotations Framework poskytuje podobnou funkci pro označování informací zobrazených v ovládacích prvcích zobrazení dokumentů WPF.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-116">Highlight annotations in Microsoft Annotations Framework provide a similar feature for marking up information displayed in WPF document viewing controls.</span></span>  
  
 <span data-ttu-id="5d1d6-117">Následující obrázek znázorňuje příklad zvýraznění poznámky.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-117">The following illustration shows an example of a highlight annotation.</span></span>  
  
 <span data-ttu-id="5d1d6-118">![Zvýraznění poznámky](./media/caf-callouts.png "CAF_Callouts")</span><span class="sxs-lookup"><span data-stu-id="5d1d6-118">![Highlight Annotation](./media/caf-callouts.png "CAF_Callouts")</span></span>  
  
 <span data-ttu-id="5d1d6-119">Uživatelé obvykle vytvářejí poznámky tak, že nejprve vybere nějaký text nebo položku, která je předmětem zájmu, a potom klepnutím pravým tlačítkem myši zobrazíte možnosti <xref:System.Windows.Controls.ContextMenu> poznámky.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-119">Users typically create annotations by first selecting some text or an item of interest, and then right-clicking to display a <xref:System.Windows.Controls.ContextMenu> of annotation options.</span></span>  <span data-ttu-id="5d1d6-120">Následující příklad [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ukazuje, jak můžete <xref:System.Windows.Controls.ContextMenu> deklarovat příkazy s směrovcí, ke kterým mají uživatelé přístup k vytváření a správě anotací.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-120">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] you can use to declare a <xref:System.Windows.Controls.ContextMenu> with routed commands that users can access to create and manage annotations.</span></span>  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>
## <a name="data-anchoring"></a><span data-ttu-id="5d1d6-121">Kotvení dat</span><span class="sxs-lookup"><span data-stu-id="5d1d6-121">Data Anchoring</span></span>  
 <span data-ttu-id="5d1d6-122">Architektura anotací váže poznámky k datům, která uživatel vybere, nikoli pouze na pozici v zobrazení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-122">The Annotations Framework binds annotations to the data that the user selects, not just to a position on the display view.</span></span> <span data-ttu-id="5d1d6-123">Proto pokud se změní zobrazení dokumentu, například když uživatel posouvá nebo mění velikost okna zobrazení, poznámky zůstane s výběrem dat, ke kterému je vázán.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-123">Therefore, if the document view changes, such as when the user scrolls or resizes the display window, the annotation stays with the data selection to which it is bound.</span></span> <span data-ttu-id="5d1d6-124">Například následující obrázek znázorňuje poznámku, kterou uživatel vytvořil při výběru textu.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-124">For example, the following graphic illustrates an annotation that the user has made on a text selection.</span></span> <span data-ttu-id="5d1d6-125">Když se zobrazení dokumentu změní (posune, změní velikost, změní velikost, změní velikost nebo se jinak přesune), zvýraznění se přesune s původním výběrem dat.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-125">When the document view changes (scrolls, resizes, scales, or otherwise moves), the highlight annotation moves with the original data selection.</span></span>  
  
 <span data-ttu-id="5d1d6-126">![Ukotvení dat poznámky](./media/caf-dataanchoring.png "CAF_DataAnchoring")</span><span class="sxs-lookup"><span data-stu-id="5d1d6-126">![Annotation Data Anchoring](./media/caf-dataanchoring.png "CAF_DataAnchoring")</span></span>  
  
<a name="matching_annotations_with_annotated_objects"></a>
## <a name="matching-annotations-with-annotated-objects"></a><span data-ttu-id="5d1d6-127">Porovnávání poznámk s objekty s poznámkami</span><span class="sxs-lookup"><span data-stu-id="5d1d6-127">Matching Annotations with Annotated Objects</span></span>  
 <span data-ttu-id="5d1d6-128">Poznámky můžete porovnat s odpovídajícími objekty s anotací.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-128">You can match annotations with the corresponding annotated objects.</span></span> <span data-ttu-id="5d1d6-129">Zvažte například jednoduchou aplikaci pro čtení dokumentů, která má podokno poznámek.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-129">For example, consider a simple document reader application that has a comments pane.</span></span> <span data-ttu-id="5d1d6-130">Podokno poznámek může být seznam, který zobrazuje text ze seznamu poznámek ukotvených v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-130">The comments pane might be a list box that displays the text from a list of annotations that are anchored to a document.</span></span> <span data-ttu-id="5d1d6-131">Pokud uživatel vybere položku v seznamu, aplikace se zobrazí do zobrazení odstavce v dokumentu, ke kterému je odpovídající objekt poznámky ukotven.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-131">If the user selects an item in the list box, then the application brings into view the paragraph in the document that the corresponding annotation object is anchored to.</span></span>  
  
 <span data-ttu-id="5d1d6-132">Následující příklad ukazuje, jak implementovat obslužnou rutinu události takového seznamu, který slouží jako podokno poznámek.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-132">The following example demonstrates how to implement the event handler of such a list box that serves as the comments pane.</span></span>  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 <span data-ttu-id="5d1d6-133">Další příklad scénáře zahrnuje aplikace, které umožňují výměnu poznámek a rychlé poznámky mezi čtečkami dokumentů prostřednictvím e-mailu.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-133">Another example scenario involves applications that enable the exchange of annotations and sticky notes between document readers through email.</span></span> <span data-ttu-id="5d1d6-134">Tato funkce umožňuje těmto aplikacím přejít čtenáře na stránku, která obsahuje poznámku, která je právě vyměňována.</span><span class="sxs-lookup"><span data-stu-id="5d1d6-134">This feature enables these applications to navigate the reader to the page that contains the annotation that is being exchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1d6-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d1d6-135">See also</span></span>

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [<span data-ttu-id="5d1d6-136">Schéma poznámek</span><span class="sxs-lookup"><span data-stu-id="5d1d6-136">Annotations Schema</span></span>](annotations-schema.md)
- [<span data-ttu-id="5d1d6-137">ContextMenu – přehled</span><span class="sxs-lookup"><span data-stu-id="5d1d6-137">ContextMenu Overview</span></span>](../controls/contextmenu-overview.md)
- [<span data-ttu-id="5d1d6-138">Přehled příkazů</span><span class="sxs-lookup"><span data-stu-id="5d1d6-138">Commanding Overview</span></span>](commanding-overview.md)
- [<span data-ttu-id="5d1d6-139">Přehled toku dokumentů</span><span class="sxs-lookup"><span data-stu-id="5d1d6-139">Flow Document Overview</span></span>](flow-document-overview.md)
- <span data-ttu-id="5d1d6-140">[Postup: Přidání příkazu do položky MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5d1d6-140">[How to: Add a Command to a MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))</span></span>
