---
title: "Přehled poznámek"
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
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc4ef4473a200a424134a16d64655a5acf1488b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="annotations-overview"></a><span data-ttu-id="b87b2-102">Přehled poznámek</span><span class="sxs-lookup"><span data-stu-id="b87b2-102">Annotations Overview</span></span>
<span data-ttu-id="b87b2-103">Zápis poznámky nebo komentáře na tištěných dokumentů je takové běžná aktivita, jsme téměř vzít pro udělena.</span><span class="sxs-lookup"><span data-stu-id="b87b2-103">Writing notes or comments on paper documents is such a commonplace activity that we almost take it for granted.</span></span> <span data-ttu-id="b87b2-104">Tyto poznámky nebo komentáře jsou "Poznámky" přidáme do dokumentu. Chcete-li příznak informace nebo chcete zvýraznit položky, které vás zajímají pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="b87b2-104">These notes or comments are "annotations" that we add to a document to flag information or to highlight items of interest for later reference.</span></span> <span data-ttu-id="b87b2-105">Zápis poznámky na tištěných dokumentů je snadné a běžné, možnost přidávat komentáře osobní do elektronických dokumentů sice obvykle velmi omezená, pokud je k dispozici na všech.</span><span class="sxs-lookup"><span data-stu-id="b87b2-105">Although writing notes on printed documents is easy and commonplace, the ability to add personal comments to electronic documents is typically very limited, if available at all.</span></span>  
  
 <span data-ttu-id="b87b2-106">Toto téma zkontroluje několik běžných typů poznámek, konkrétně rychlé poznámky a označuje a ukazuje, jak [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] usnadňuje tyto typy poznámky v aplikacích pomocí [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] dokumentu zobrazení ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="b87b2-106">This topic reviews several common types of annotations, specifically sticky notes and highlights, and illustrates how the [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] facilitates these types of annotations in applications through the [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] document viewing controls.</span></span>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="b87b2-107">ovládací prvky zobrazení dokumentu, které podporují poznámky zahrnují <xref:System.Windows.Controls.FlowDocumentReader> a <xref:System.Windows.Controls.FlowDocumentScrollViewer>, stejně jako ovládacích prvků odvozených z <xref:System.Windows.Controls.Primitives.DocumentViewerBase> například <xref:System.Windows.Controls.DocumentViewer> a <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span><span class="sxs-lookup"><span data-stu-id="b87b2-107"> document viewing controls that support annotations include <xref:System.Windows.Controls.FlowDocumentReader> and <xref:System.Windows.Controls.FlowDocumentScrollViewer>, as well as controls derived from <xref:System.Windows.Controls.Primitives.DocumentViewerBase> such as <xref:System.Windows.Controls.DocumentViewer> and <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span></span>  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a><span data-ttu-id="b87b2-108">Rychlé poznámky</span><span class="sxs-lookup"><span data-stu-id="b87b2-108">Sticky Notes</span></span>  
 <span data-ttu-id="b87b2-109">Typické rychlé poznámky obsahuje informace, které zapisují na malou část barevný papír, který se potom "zasekla" na dokument.</span><span class="sxs-lookup"><span data-stu-id="b87b2-109">A typical sticky note contains information written on a small piece of colored paper that is then "stuck" to a document.</span></span> <span data-ttu-id="b87b2-110">Digitální rychlé poznámky poskytují podobné funkce pro elektronických dokumentů, ale flexibilnější zahrnout mnoho dalších typů obsahu, jako zadaný text, psané poznámky (například [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "ink" tahy), nebo webové odkazy.</span><span class="sxs-lookup"><span data-stu-id="b87b2-110">Digital sticky notes provide similar functionality for electronic documents, but with the added flexibility to include many other types of content such as typed text, handwritten notes (for example, [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "ink" strokes), or Web links.</span></span>  
  
 <span data-ttu-id="b87b2-111">Následující obrázek znázorňuje některé příklady zvýraznění textu rychlé poznámky a rukopisu poznámky rychlé poznámky.</span><span class="sxs-lookup"><span data-stu-id="b87b2-111">The following illustration shows some examples of highlight, text sticky note, and ink sticky note annotations.</span></span>  
  
 <span data-ttu-id="b87b2-112">![Zvýraznění, textu a rukopisu rychlé poznámky poznámky. ] (../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")</span><span class="sxs-lookup"><span data-stu-id="b87b2-112">![Highlight, text and ink sticky note annotations.](../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")</span></span>  
  
 <span data-ttu-id="b87b2-113">Následující příklad ukazuje metodu, která můžete použít k povolení podpory poznámky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b87b2-113">The following example shows the method that you can use to enable annotation support in your application.</span></span>  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a><span data-ttu-id="b87b2-114">Označuje</span><span class="sxs-lookup"><span data-stu-id="b87b2-114">Highlights</span></span>  
 <span data-ttu-id="b87b2-115">Lidí používá tvůrčí metody k upozornění k položkám, které vás zajímají při jejich vyznačení dokumentu dokumentu, například podtržení, zvýraznění, zeměkoule slova ve větě nebo kreslení značky nebo zápisy na okraji stránky.</span><span class="sxs-lookup"><span data-stu-id="b87b2-115">People use creative methods to draw attention to items of interest when they mark up a paper document, such as underlining, highlighting, circling words in a sentence, or drawing marks or notations in the margin.</span></span>  <span data-ttu-id="b87b2-116">Zvýrazněte poznámky v [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] poskytují podobné funkce pro označování informace zobrazené v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dokumentu zobrazení ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="b87b2-116">Highlight annotations in [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] provide a similar feature for marking up information displayed in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] document viewing controls.</span></span>  
  
 <span data-ttu-id="b87b2-117">Následující obrázek znázorňuje příklad poznámky zvýraznění.</span><span class="sxs-lookup"><span data-stu-id="b87b2-117">The following illustration shows an example of a highlight annotation.</span></span>  
  
 <span data-ttu-id="b87b2-118">![Zvýrazněte poznámky](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")</span><span class="sxs-lookup"><span data-stu-id="b87b2-118">![Highlight Annotation](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")</span></span>  
  
 <span data-ttu-id="b87b2-119">Uživatelé obvykle vytvářet poznámky nejprve výběrem nějaký text nebo položku, která vás zajímají, a klikněte pravým tlačítkem myši zobrazíte <xref:System.Windows.Controls.ContextMenu> možností anotace.</span><span class="sxs-lookup"><span data-stu-id="b87b2-119">Users typically create annotations by first selecting some text or an item of interest, and then right-clicking to display a <xref:System.Windows.Controls.ContextMenu> of annotation options.</span></span>  <span data-ttu-id="b87b2-120">Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] můžete deklarovat <xref:System.Windows.Controls.ContextMenu> s směrované příkazy, které mohou uživatelé vytvářet a spravovat poznámky.</span><span class="sxs-lookup"><span data-stu-id="b87b2-120">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] you can use to declare a <xref:System.Windows.Controls.ContextMenu> with routed commands that users can access to create and manage annotations.</span></span>  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a><span data-ttu-id="b87b2-121">Ukotvení dat</span><span class="sxs-lookup"><span data-stu-id="b87b2-121">Data Anchoring</span></span>  
 <span data-ttu-id="b87b2-122">[!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] Váže poznámky k datům, které uživatel vybere, ne jenom na pozici na zobrazení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="b87b2-122">The [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] binds annotations to the data that the user selects, not just to a position on the display view.</span></span> <span data-ttu-id="b87b2-123">Proto pokud se změní zobrazení dokumentů, například pokud uživatel posune nebo se změní velikost okna zobrazení anotace zůstává s výběr dat, ke kterému je vázán.</span><span class="sxs-lookup"><span data-stu-id="b87b2-123">Therefore, if the document view changes, such as when the user scrolls or resizes the display window, the annotation stays with the data selection to which it is bound.</span></span> <span data-ttu-id="b87b2-124">Například znázorněný na následujícím obrázku, který uživatel provede na výběr textu poznámky.</span><span class="sxs-lookup"><span data-stu-id="b87b2-124">For example, the following graphic illustrates an annotation that the user has made on a text selection.</span></span> <span data-ttu-id="b87b2-125">Pokud dokument zobrazit změny (viditelné, změní velikost, škály nebo jinak přesune), zvýraznění poznámky se přesune s původní výběr dat.</span><span class="sxs-lookup"><span data-stu-id="b87b2-125">When the document view changes (scrolls, resizes, scales, or otherwise moves), the highlight annotation moves with the original data selection.</span></span>  
  
 <span data-ttu-id="b87b2-126">![Ukotvení poznámky Data](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")</span><span class="sxs-lookup"><span data-stu-id="b87b2-126">![Annotation Data Anchoring](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")</span></span>  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a><span data-ttu-id="b87b2-127">Odpovídající poznámky s poznámkami objekty</span><span class="sxs-lookup"><span data-stu-id="b87b2-127">Matching Annotations with Annotated Objects</span></span>  
 <span data-ttu-id="b87b2-128">Můžete vybrat stejné poznámky s odpovídajícími poznámkami objekty.</span><span class="sxs-lookup"><span data-stu-id="b87b2-128">You can match annotations with the corresponding annotated objects.</span></span> <span data-ttu-id="b87b2-129">Představte si třeba aplikaci čtečky jednoduché dokumentu, která má podokně komentáře.</span><span class="sxs-lookup"><span data-stu-id="b87b2-129">For example, consider a simple document reader application that has a comments pane.</span></span> <span data-ttu-id="b87b2-130">V podokně komentáře může být pole se seznamem, který zobrazí text ze seznamu poznámky, které jsou ukotvené do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b87b2-130">The comments pane might be a list box that displays the text from a list of annotations that are anchored to a document.</span></span> <span data-ttu-id="b87b2-131">Pokud uživatel vybere položku v seznamu, pak aplikace přenese do zobrazení odstavce v dokumentu, který je ukotven odpovídající objektu poznámky.</span><span class="sxs-lookup"><span data-stu-id="b87b2-131">If the user selects an item in the list box, then the application brings into view the paragraph in the document that the corresponding annotation object is anchored to.</span></span>  
  
 <span data-ttu-id="b87b2-132">Následující příklad ukazuje, jak implementovat obslužné rutiny události z takových seznamu, který slouží jako podokně komentáře.</span><span class="sxs-lookup"><span data-stu-id="b87b2-132">The following example demonstrates how to implement the event handler of such a list box that serves as the comments pane.</span></span>  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 <span data-ttu-id="b87b2-133">Jiný příklad scénáře zahrnuje aplikace, které umožňují exchange poznámky a rychlé poznámky čtenářů dokumentu prostřednictvím e-mailu.</span><span class="sxs-lookup"><span data-stu-id="b87b2-133">Another example scenario involves applications that enable the exchange of annotations and sticky notes between document readers through e-mail.</span></span> <span data-ttu-id="b87b2-134">Tato funkce umožňuje tyto aplikace a přejděte na stránku, který obsahuje poznámky, které se vyměňují čtečky.</span><span class="sxs-lookup"><span data-stu-id="b87b2-134">This feature enables these applications to navigate the reader to the page that contains the annotation that is being exchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87b2-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="b87b2-135">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>  
 <xref:System.Windows.Controls.DocumentViewer>  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>  
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
 <xref:System.Windows.Controls.FlowDocumentReader>  
 <xref:System.Windows.Annotations.IAnchorInfo>  
 [<span data-ttu-id="b87b2-136">Schéma poznámky</span><span class="sxs-lookup"><span data-stu-id="b87b2-136">Annotations Schema</span></span>](../../../../docs/framework/wpf/advanced/annotations-schema.md)  
 [<span data-ttu-id="b87b2-137">ContextMenu – přehled</span><span class="sxs-lookup"><span data-stu-id="b87b2-137">ContextMenu Overview</span></span>](../../../../docs/framework/wpf/controls/contextmenu-overview.md)  
 [<span data-ttu-id="b87b2-138">Tvorba příkazů – přehled</span><span class="sxs-lookup"><span data-stu-id="b87b2-138">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="b87b2-139">Přehled toku dokumentu</span><span class="sxs-lookup"><span data-stu-id="b87b2-139">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="b87b2-140">Postupy: přidání příkazu do MenuItem</span><span class="sxs-lookup"><span data-stu-id="b87b2-140">How to: Add a Command to a MenuItem</span></span>](http://msdn.microsoft.com/en-us/013d68a0-5373-4a68-bd91-5de574307370)
