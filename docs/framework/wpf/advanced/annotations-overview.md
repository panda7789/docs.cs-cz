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
ms.openlocfilehash: 80555ad714ffe5cab6722d2d6d45fb6a6bb45609
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="annotations-overview"></a>Přehled poznámek
Zápis poznámky nebo komentáře na tištěných dokumentů je takové běžná aktivita, jsme téměř vzít pro udělena. Tyto poznámky nebo komentáře jsou "Poznámky" přidáme do dokumentu. Chcete-li příznak informace nebo chcete zvýraznit položky, které vás zajímají pro pozdější použití. Zápis poznámky na tištěných dokumentů je snadné a běžné, možnost přidávat komentáře osobní do elektronických dokumentů sice obvykle velmi omezená, pokud je k dispozici na všech.  
  
 Toto téma zkontroluje několik běžných typů poznámek, konkrétně rychlé poznámky a označuje a ukazuje, jak [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] usnadňuje tyto typy poznámky v aplikacích prostřednictvím dokumentu Windows Presentation Foundation (WPF) zobrazení ovládacích prvků.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ovládací prvky zobrazení dokumentu, které podporují poznámky zahrnují <xref:System.Windows.Controls.FlowDocumentReader> a <xref:System.Windows.Controls.FlowDocumentScrollViewer>, stejně jako ovládacích prvků odvozených z <xref:System.Windows.Controls.Primitives.DocumentViewerBase> například <xref:System.Windows.Controls.DocumentViewer> a <xref:System.Windows.Controls.FlowDocumentPageViewer>.  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Rychlé poznámky  
 Typické rychlé poznámky obsahuje informace, které zapisují na malou část barevný papír, který se potom "zasekla" na dokument. Digitální rychlé poznámky poskytují podobné funkce pro elektronických dokumentů, ale flexibilnější zahrnout mnoho dalších typů obsahu, jako zadaný text, psané poznámky (například [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "ink" tahy), nebo webové odkazy.  
  
 Následující obrázek znázorňuje některé příklady zvýraznění textu rychlé poznámky a rukopisu poznámky rychlé poznámky.  
  
 ![Zvýraznění, textu a rukopisu rychlé poznámky poznámky. ] (../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Následující příklad ukazuje metodu, která můžete použít k povolení podpory poznámky v aplikaci.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Označuje  
 Lidí používá tvůrčí metody k upozornění k položkám, které vás zajímají při jejich vyznačení dokumentu dokumentu, například podtržení, zvýraznění, zeměkoule slova ve větě nebo kreslení značky nebo zápisy na okraji stránky.  Zvýrazněte poznámky v [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] poskytují podobné funkce pro označování informace zobrazené v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dokumentu zobrazení ovládacích prvků.  
  
 Následující obrázek znázorňuje příklad poznámky zvýraznění.  
  
 ![Zvýrazněte poznámky](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")  
  
 Uživatelé obvykle vytvářet poznámky nejprve výběrem nějaký text nebo položku, která vás zajímají, a klikněte pravým tlačítkem myši zobrazíte <xref:System.Windows.Controls.ContextMenu> možností anotace.  Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] můžete deklarovat <xref:System.Windows.Controls.ContextMenu> s směrované příkazy, které mohou uživatelé vytvářet a spravovat poznámky.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Ukotvení dat  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] Váže poznámky k datům, které uživatel vybere, ne jenom na pozici na zobrazení zobrazení. Proto pokud se změní zobrazení dokumentů, například pokud uživatel posune nebo se změní velikost okna zobrazení anotace zůstává s výběr dat, ke kterému je vázán. Například znázorněný na následujícím obrázku, který uživatel provede na výběr textu poznámky. Pokud dokument zobrazit změny (viditelné, změní velikost, škály nebo jinak přesune), zvýraznění poznámky se přesune s původní výběr dat.  
  
 ![Ukotvení poznámky Data](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Odpovídající poznámky s poznámkami objekty  
 Můžete vybrat stejné poznámky s odpovídajícími poznámkami objekty. Představte si třeba aplikaci čtečky jednoduché dokumentu, která má podokně komentáře. V podokně komentáře může být pole se seznamem, který zobrazí text ze seznamu poznámky, které jsou ukotvené do dokumentu. Pokud uživatel vybere položku v seznamu, pak aplikace přenese do zobrazení odstavce v dokumentu, který je ukotven odpovídající objektu poznámky.  
  
 Následující příklad ukazuje, jak implementovat obslužné rutiny události z takových seznamu, který slouží jako podokně komentáře.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Jiný příklad scénáře zahrnuje aplikace, které umožňují exchange poznámky a rychlé poznámky čtenářů dokumentu e-mailem. Tato funkce umožňuje tyto aplikace a přejděte na stránku, který obsahuje poznámky, které se vyměňují čtečky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>  
 <xref:System.Windows.Controls.DocumentViewer>  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>  
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
 <xref:System.Windows.Controls.FlowDocumentReader>  
 <xref:System.Windows.Annotations.IAnchorInfo>  
 [Schéma poznámek](../../../../docs/framework/wpf/advanced/annotations-schema.md)  
 [ContextMenu – přehled](../../../../docs/framework/wpf/controls/contextmenu-overview.md)  
 [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Postupy: přidání příkazu do MenuItem](http://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)
