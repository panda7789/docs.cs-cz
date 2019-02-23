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
ms.openlocfilehash: e88383126c1fb618b2a2a96bdf5998560864af50
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746439"
---
# <a name="annotations-overview"></a>Přehled poznámek
Zápis poznámky nebo komentáře k dokumentu dokumentů je takový běžnou aktivitu, že jsme téměř jít samozřejmost. Tyto poznámky nebo komentáře jsou "Poznámky" přidáme do dokumentu označit, že informace nebo chcete zvýraznit položky relevantní pro pozdější použití. I když zápis poznámky na dokumenty tištěné je snadné a běžné, možnost přidávat vlastní komentář elektronických dokumentů je obvykle velmi omezená, pokud je k dispozici ve všech.  
  
 Toto téma kontroluje několik běžných typů poznámek, konkrétně rychlé poznámky a zvýraznění a ukazuje, jak [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] usnadňuje tyto typy poznámek v aplikacích v dokumentu Windows Presentation Foundation (WPF) zobrazení ovládacích prvků.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zobrazení ovládacích prvků dokumentu, které podporují poznámky zahrnují <xref:System.Windows.Controls.FlowDocumentReader> a <xref:System.Windows.Controls.FlowDocumentScrollViewer>, stejně jako ovládací prvky je odvozena z <xref:System.Windows.Controls.Primitives.DocumentViewerBase> například <xref:System.Windows.Controls.DocumentViewer> a <xref:System.Windows.Controls.FlowDocumentPageViewer>.  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Rychlé poznámky  
 Typické poznámku obsahuje informace napsané na malou část barevného papíru, který se potom "zasekla" na dokument. Digitální rychlých poznámek poskytuje podobné funkce pro elektronických dokumentů, ale s vyšší flexibilitu zahrnout mnoho jiných typů obsahu, jako zadaný text, ručně psaných poznámek (například [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "inkoustu" tahy), nebo webové odkazy.  
  
 Následující obrázek znázorňuje několik příkladů zvýraznění textu poznámku a ink poznámku poznámky.  
  
 ![Zvýraznění, text a ink rychlých poznámek. ](../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Následující příklad ukazuje metodu, která můžete použít k povolení anotace podpory ve vaší aplikaci.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Vybraná vystoupení  
 Lidé použít creative metody k přitažení pozornosti ke položky, které vás zajímají, když se označit dokument papíru, jako je například podtržení, zvýraznění, zeměkoule slova ve větě nebo vykreslení značek nebo zápisy na okraji.  Zvýrazněte poznámky v [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] poskytuje podobné funkce pro označení informace zobrazené v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dokumentu, zobrazení ovládacích prvků.  
  
 Následující obrázek znázorňuje příklad poznámky zvýraznění.  
  
 ![Zvýrazněte anotace](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")  
  
 Uživatelé obvykle vytvoříte nejprve vyberete nějaký text nebo položky, které vás zajímají, a klikněte pravým tlačítkem myši zobrazíte poznámky <xref:System.Windows.Controls.ContextMenu> možností anotace.  Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] můžete použít k deklaraci <xref:System.Windows.Controls.ContextMenu> s směrované příkazy, které mohou uživatelé vytvářet a spravovat poznámky.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Ukotvení dat  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] Váže poznámky o datech, která uživatel vybere, ne jenom na pozici na zobrazení zobrazení. Proto pokud se změní zobrazení dokumentu, například když uživatel posune nebo změní velikost okna zobrazení Poznámka zůstane se výběr dat, ke kterému je vázán. Následující obrázek například znázorňuje anotaci, která uživatel provedl ve výběru textu. Pokud dokument zobrazit změny (posouvá, změny velikosti, měřítka nebo jinak přesune), anotace zvýraznění se přesune s původní výběr data.  
  
 ![Ukotvení poznámky Data](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Odpovídající poznámky s objekty s poznámkami  
 Můžete porovnat poznámky s odpovídajícími objekty s poznámkami. Zvažte například aplikaci čtečky jednoduché dokumentu, která má podokně komentáře. V podokně komentáře je možné pole se seznamem, který zobrazí text ze seznamu poznámky, které jsou ukotveny na dokument. Pokud si uživatel vybere položku v seznamu, pak aplikace přináší do zobrazení odstavce v dokumentu, který je ukotven odpovídajícího objektu poznámky.  
  
 Následující příklad ukazuje, jak implementovat obslužná rutina události takové seznamu, která slouží jako podokně komentáře.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Jiný ukázkový scénář zahrnuje aplikace, které umožňují výměny poznámky a rychlých poznámek čtenářů dokumentu e-mailem. Tato funkce umožňuje tyto aplikace pro navigaci čtenáře na stránce, která obsahuje poznámky, které se vyměňují.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [Schéma poznámek](../../../../docs/framework/wpf/advanced/annotations-schema.md)
- [ContextMenu – přehled](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
- [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)
- [Přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
- [Postupy: Přidání příkazu do položku nabídky](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
