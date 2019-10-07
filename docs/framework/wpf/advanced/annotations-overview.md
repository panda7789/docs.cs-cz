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
ms.openlocfilehash: dc9c4125f9ac3c44be41efe92b9e495599e5c130
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004045"
---
# <a name="annotations-overview"></a>Přehled poznámek
Zápis poznámek nebo komentářů k dokumentům je taková maloobchodech aktivita, kterou pro udělení máme skoro. Tyto poznámky nebo komentáře jsou "poznámky", které přidáváme do dokumentu k označení informací, nebo k zdůraznění položek, které vás zajímají za účelem pozdějšího odkazu. I když píšete poznámky k tištěným dokumentům snadno a maloobchodech, možnost přidávat osobní komentáře k elektronickým dokumentům je obvykle velmi omezená, pokud je k dispozici vůbec.  
  
 Toto téma posuzuje několik běžných typů poznámek, konkrétně rychlé poznámky a světla, a ukazuje, jak rozhraní Microsoft anotace usnadňuje tyto typy poznámek v aplikacích prostřednictvím Windows Presentation Foundation (WPF ) ovládací prvky zobrazení dokumentu.  @no__t – 0 ovládací prvky, které podporují poznámky, zahrnují <xref:System.Windows.Controls.FlowDocumentReader> a <xref:System.Windows.Controls.FlowDocumentScrollViewer>, a také ovládací prvky odvozené od <xref:System.Windows.Controls.Primitives.DocumentViewerBase>, například <xref:System.Windows.Controls.DocumentViewer> a <xref:System.Windows.Controls.FlowDocumentPageViewer>.  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Rychlé poznámky  
 Typická rychlá Poznámka obsahuje informace napsané na malém barevném papíru, který je pak zablokovaný do dokumentu. Digitální rychlé poznámky poskytují podobné funkce pro elektronické dokumenty, ale díky flexibilní flexibilitě můžete zahrnout mnoho dalších typů obsahu, jako je například zadaný text, rukopisné poznámky (například tahy perem tabletu) nebo webové odkazy.  
  
 Následující ilustrace znázorňuje některé příklady zvýraznění, text v rychlé poznámce a rukopisné poznámky k rychlé poznámce.  
  
 ![Zvýrazňovat, text a rukopisné poznámky k rychlé poznámce.](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Následující příklad ukazuje metodu, kterou můžete použít k povolení podpory poznámek ve vaší aplikaci.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Růžov  
 Lidé používají kreativní metody k upoutání pozornosti na zajímavé položky, když označí dokument papíru, jako je například podtržení, zvýraznění, směřující slova ve větě nebo kreslení značek nebo zápisů na okraji.  Zvýrazněné poznámky v rozhraní Microsoft anotace poskytují podobnou funkci pro označení informací zobrazených v ovládacích prvcích zobrazení dokumentů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 Následující ilustrace znázorňuje příklad poznámky zvýraznění.  
  
 ![Zvýraznit anotaci](./media/caf-callouts.png "CAF_Callouts")  
  
 Uživatelé obvykle vytvářejí poznámky tak, že nejprve vyberou nějaký text nebo položku zájmu a potom kliknutím pravým tlačítkem zobrazí @no__t možnosti poznámky.  Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít k deklaraci <xref:System.Windows.Controls.ContextMenu> s směrovanými příkazy, ke kterým mají uživatelé přístup k vytváření a správě poznámek.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Ukotvení dat  
 Rozhraní anotace váže poznámky k datům, která uživatel vybere, nikoli pouze k pozici v zobrazení zobrazení. Proto pokud se dokument zobrazí změny, například když uživatel posune nebo změní velikost okna zobrazení, Poznámka zůstane s výběrem dat, ke kterému je vázáno. Například následující obrázek znázorňuje poznámku, kterou uživatel vytvořil na výběr textu. Při změně zobrazení dokumentu (posouvání, změna velikosti, škálování nebo jiné přesunutí) se zvýrazněná Poznámka přesune s výběrem původní data.  
  
 (./media/caf-dataanchoring.png "CAF_DataAnchoring") ![ukotvení dat poznámek]  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Porovnávací poznámky s poznámkami objektů  
 Poznámky můžete porovnávat s odpovídajícími objekty s poznámkami. Zvažte například jednoduchou aplikaci pro čtení dokumentů, která obsahuje podokno komentáře. Podokno komentáře může být seznam, ve kterém se zobrazí text ze seznamu poznámek, které jsou ukotveny k dokumentu. Pokud uživatel vybere položku v seznamu, aplikace se zobrazí v dokumentu, na který je ukotven odpovídající objekt poznámky.  
  
 Následující příklad ukazuje, jak implementovat obslužnou rutinu události takového seznamu, který slouží jako podokno komentáře.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Další ukázkový scénář zahrnuje aplikace, které umožňují výměnu poznámek a rychlých poznámek mezi čtečkami dokumentů prostřednictvím e-mailu. Tato funkce umožňuje těmto aplikacím procházet čtečku na stránku, která obsahuje poznámku, která se právě vyměňují.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [Schéma poznámek](annotations-schema.md)
- [ContextMenu – přehled](../controls/contextmenu-overview.md)
- [Přehled příkazů](commanding-overview.md)
- [Přehled toku dokumentů](flow-document-overview.md)
- [Postupy: Přidání příkazu do nabídky MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
