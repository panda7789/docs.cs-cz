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
ms.openlocfilehash: b82c7e7300ebc295ca06d565c2fb5f6f2b28e92c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636507"
---
# <a name="annotations-overview"></a><span data-ttu-id="9a208-102">Přehled poznámek</span><span class="sxs-lookup"><span data-stu-id="9a208-102">Annotations Overview</span></span>
<span data-ttu-id="9a208-103">Zápis poznámek nebo komentářů k dokumentům je taková maloobchodech aktivita, kterou pro udělení máme skoro.</span><span class="sxs-lookup"><span data-stu-id="9a208-103">Writing notes or comments on paper documents is such a commonplace activity that we almost take it for granted.</span></span> <span data-ttu-id="9a208-104">Tyto poznámky nebo komentáře jsou "poznámky", které přidáváme do dokumentu k označení informací, nebo k zdůraznění položek, které vás zajímají za účelem pozdějšího odkazu.</span><span class="sxs-lookup"><span data-stu-id="9a208-104">These notes or comments are "annotations" that we add to a document to flag information or to highlight items of interest for later reference.</span></span> <span data-ttu-id="9a208-105">I když píšete poznámky k tištěným dokumentům snadno a maloobchodech, možnost přidávat osobní komentáře k elektronickým dokumentům je obvykle velmi omezená, pokud je k dispozici vůbec.</span><span class="sxs-lookup"><span data-stu-id="9a208-105">Although writing notes on printed documents is easy and commonplace, the ability to add personal comments to electronic documents is typically very limited, if available at all.</span></span>  
  
 <span data-ttu-id="9a208-106">Toto téma posuzuje několik běžných typů poznámek, konkrétně rychlé poznámky a světla, a ukazuje, jak rozhraní Microsoft anotace usnadňuje tyto typy poznámek v aplikacích prostřednictvím Windows Presentation Foundation (WPF ) ovládací prvky zobrazení dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9a208-106">This topic reviews several common types of annotations, specifically sticky notes and highlights, and illustrates how the Microsoft Annotations Framework facilitates these types of annotations in applications through the Windows Presentation Foundation (WPF) document viewing controls.</span></span>  <span data-ttu-id="9a208-107">Ovládací prvky pro zobrazení dokumentu WPF, které podporují poznámky, zahrnují <xref:System.Windows.Controls.FlowDocumentReader> a <xref:System.Windows.Controls.FlowDocumentScrollViewer>a také ovládací prvky odvozené od <xref:System.Windows.Controls.Primitives.DocumentViewerBase>, jako jsou <xref:System.Windows.Controls.DocumentViewer> a <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span><span class="sxs-lookup"><span data-stu-id="9a208-107">WPF document viewing controls that support annotations include <xref:System.Windows.Controls.FlowDocumentReader> and <xref:System.Windows.Controls.FlowDocumentScrollViewer>, as well as controls derived from <xref:System.Windows.Controls.Primitives.DocumentViewerBase> such as <xref:System.Windows.Controls.DocumentViewer> and <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span></span>  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a><span data-ttu-id="9a208-108">Rychlé poznámky</span><span class="sxs-lookup"><span data-stu-id="9a208-108">Sticky Notes</span></span>  
 <span data-ttu-id="9a208-109">Typická rychlá Poznámka obsahuje informace napsané na malém barevném papíru, který je pak zablokovaný do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9a208-109">A typical sticky note contains information written on a small piece of colored paper that is then "stuck" to a document.</span></span> <span data-ttu-id="9a208-110">Digitální rychlé poznámky poskytují podobné funkce pro elektronické dokumenty, ale díky flexibilní flexibilitě můžete zahrnout mnoho dalších typů obsahu, jako je například zadaný text, rukopisné poznámky (například tahy perem tabletu) nebo webové odkazy.</span><span class="sxs-lookup"><span data-stu-id="9a208-110">Digital sticky notes provide similar functionality for electronic documents, but with the added flexibility to include many other types of content such as typed text, handwritten notes (for example, Tablet PC "ink" strokes), or Web links.</span></span>  
  
 <span data-ttu-id="9a208-111">Následující ilustrace znázorňuje některé příklady zvýraznění, text v rychlé poznámce a rukopisné poznámky k rychlé poznámce.</span><span class="sxs-lookup"><span data-stu-id="9a208-111">The following illustration shows some examples of highlight, text sticky note, and ink sticky note annotations.</span></span>  
  
 <span data-ttu-id="9a208-112">![Zvýrazňovat, text a rukopisné poznámky k rychlé poznámce.](./media/caf-stickynote.jpg "CAF_StickyNote")</span><span class="sxs-lookup"><span data-stu-id="9a208-112">![Highlight, text and ink sticky note annotations.](./media/caf-stickynote.jpg "CAF_StickyNote")</span></span>  
  
 <span data-ttu-id="9a208-113">Následující příklad ukazuje metodu, kterou můžete použít k povolení podpory poznámek ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9a208-113">The following example shows the method that you can use to enable annotation support in your application.</span></span>  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a><span data-ttu-id="9a208-114">Hlavní body</span><span class="sxs-lookup"><span data-stu-id="9a208-114">Highlights</span></span>  
 <span data-ttu-id="9a208-115">Lidé používají kreativní metody k upoutání pozornosti na zajímavé položky, když označí dokument papíru, jako je například podtržení, zvýraznění, směřující slova ve větě nebo kreslení značek nebo zápisů na okraji.</span><span class="sxs-lookup"><span data-stu-id="9a208-115">People use creative methods to draw attention to items of interest when they mark up a paper document, such as underlining, highlighting, circling words in a sentence, or drawing marks or notations in the margin.</span></span>  <span data-ttu-id="9a208-116">Zvýrazněné poznámky v rozhraní Microsoft anotace poskytují podobnou funkci pro označení informací zobrazených v ovládacích prvcích zobrazení dokumentů WPF.</span><span class="sxs-lookup"><span data-stu-id="9a208-116">Highlight annotations in Microsoft Annotations Framework provide a similar feature for marking up information displayed in WPF document viewing controls.</span></span>  
  
 <span data-ttu-id="9a208-117">Následující ilustrace znázorňuje příklad poznámky zvýraznění.</span><span class="sxs-lookup"><span data-stu-id="9a208-117">The following illustration shows an example of a highlight annotation.</span></span>  
  
 <span data-ttu-id="9a208-118">![Zvýraznit poznámku](./media/caf-callouts.png "CAF_Callouts")</span><span class="sxs-lookup"><span data-stu-id="9a208-118">![Highlight Annotation](./media/caf-callouts.png "CAF_Callouts")</span></span>  
  
 <span data-ttu-id="9a208-119">Uživatelé obvykle vytvářejí poznámky tak, že nejprve vyberou nějaký text nebo položku zájmu a potom kliknutím pravým tlačítkem zobrazí <xref:System.Windows.Controls.ContextMenu> možností poznámek.</span><span class="sxs-lookup"><span data-stu-id="9a208-119">Users typically create annotations by first selecting some text or an item of interest, and then right-clicking to display a <xref:System.Windows.Controls.ContextMenu> of annotation options.</span></span>  <span data-ttu-id="9a208-120">Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] můžete použít k deklaraci <xref:System.Windows.Controls.ContextMenu> s směrovanými příkazy, ke kterým mají uživatelé přístup, aby mohli vytvářet a spravovat poznámky.</span><span class="sxs-lookup"><span data-stu-id="9a208-120">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] you can use to declare a <xref:System.Windows.Controls.ContextMenu> with routed commands that users can access to create and manage annotations.</span></span>  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a><span data-ttu-id="9a208-121">Ukotvení dat</span><span class="sxs-lookup"><span data-stu-id="9a208-121">Data Anchoring</span></span>  
 <span data-ttu-id="9a208-122">Rozhraní anotace váže poznámky k datům, která uživatel vybere, nikoli pouze k pozici v zobrazení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9a208-122">The Annotations Framework binds annotations to the data that the user selects, not just to a position on the display view.</span></span> <span data-ttu-id="9a208-123">Proto pokud se dokument zobrazí změny, například když uživatel posune nebo změní velikost okna zobrazení, Poznámka zůstane s výběrem dat, ke kterému je vázáno.</span><span class="sxs-lookup"><span data-stu-id="9a208-123">Therefore, if the document view changes, such as when the user scrolls or resizes the display window, the annotation stays with the data selection to which it is bound.</span></span> <span data-ttu-id="9a208-124">Například následující obrázek znázorňuje poznámku, kterou uživatel vytvořil na výběr textu.</span><span class="sxs-lookup"><span data-stu-id="9a208-124">For example, the following graphic illustrates an annotation that the user has made on a text selection.</span></span> <span data-ttu-id="9a208-125">Při změně zobrazení dokumentu (posouvání, změna velikosti, škálování nebo jiné přesunutí) se zvýrazněná Poznámka přesune s výběrem původní data.</span><span class="sxs-lookup"><span data-stu-id="9a208-125">When the document view changes (scrolls, resizes, scales, or otherwise moves), the highlight annotation moves with the original data selection.</span></span>  
  
 <span data-ttu-id="9a208-126">![Ukotvení dat poznámek](./media/caf-dataanchoring.png "CAF_DataAnchoring")</span><span class="sxs-lookup"><span data-stu-id="9a208-126">![Annotation Data Anchoring](./media/caf-dataanchoring.png "CAF_DataAnchoring")</span></span>  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a><span data-ttu-id="9a208-127">Porovnávací poznámky s poznámkami objektů</span><span class="sxs-lookup"><span data-stu-id="9a208-127">Matching Annotations with Annotated Objects</span></span>  
 <span data-ttu-id="9a208-128">Poznámky můžete porovnávat s odpovídajícími objekty s poznámkami.</span><span class="sxs-lookup"><span data-stu-id="9a208-128">You can match annotations with the corresponding annotated objects.</span></span> <span data-ttu-id="9a208-129">Zvažte například jednoduchou aplikaci pro čtení dokumentů, která obsahuje podokno komentáře.</span><span class="sxs-lookup"><span data-stu-id="9a208-129">For example, consider a simple document reader application that has a comments pane.</span></span> <span data-ttu-id="9a208-130">Podokno komentáře může být seznam, ve kterém se zobrazí text ze seznamu poznámek, které jsou ukotveny k dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9a208-130">The comments pane might be a list box that displays the text from a list of annotations that are anchored to a document.</span></span> <span data-ttu-id="9a208-131">Pokud uživatel vybere položku v seznamu, aplikace se zobrazí v dokumentu, na který je ukotven odpovídající objekt poznámky.</span><span class="sxs-lookup"><span data-stu-id="9a208-131">If the user selects an item in the list box, then the application brings into view the paragraph in the document that the corresponding annotation object is anchored to.</span></span>  
  
 <span data-ttu-id="9a208-132">Následující příklad ukazuje, jak implementovat obslužnou rutinu události takového seznamu, který slouží jako podokno komentáře.</span><span class="sxs-lookup"><span data-stu-id="9a208-132">The following example demonstrates how to implement the event handler of such a list box that serves as the comments pane.</span></span>  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 <span data-ttu-id="9a208-133">Další ukázkový scénář zahrnuje aplikace, které umožňují výměnu poznámek a rychlých poznámek mezi čtečkami dokumentů prostřednictvím e-mailu.</span><span class="sxs-lookup"><span data-stu-id="9a208-133">Another example scenario involves applications that enable the exchange of annotations and sticky notes between document readers through email.</span></span> <span data-ttu-id="9a208-134">Tato funkce umožňuje těmto aplikacím procházet čtečku na stránku, která obsahuje poznámku, která se právě vyměňují.</span><span class="sxs-lookup"><span data-stu-id="9a208-134">This feature enables these applications to navigate the reader to the page that contains the annotation that is being exchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a208-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a208-135">See also</span></span>

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [<span data-ttu-id="9a208-136">Schéma poznámek</span><span class="sxs-lookup"><span data-stu-id="9a208-136">Annotations Schema</span></span>](annotations-schema.md)
- [<span data-ttu-id="9a208-137">ContextMenu – přehled</span><span class="sxs-lookup"><span data-stu-id="9a208-137">ContextMenu Overview</span></span>](../controls/contextmenu-overview.md)
- [<span data-ttu-id="9a208-138">Přehled příkazů</span><span class="sxs-lookup"><span data-stu-id="9a208-138">Commanding Overview</span></span>](commanding-overview.md)
- [<span data-ttu-id="9a208-139">Přehled toku dokumentů</span><span class="sxs-lookup"><span data-stu-id="9a208-139">Flow Document Overview</span></span>](flow-document-overview.md)
- <span data-ttu-id="9a208-140">[Postupy: Přidání příkazu do nabídky MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9a208-140">[How to: Add a Command to a MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))</span></span>
