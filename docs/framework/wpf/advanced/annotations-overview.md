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
# <a name="annotations-overview"></a>Přehled poznámek
Psaní poznámek nebo komentářů na papírových dokumentech je tak běžná činnost, že ji téměř považujeme za samozřejmou. Tyto poznámky nebo komentáře jsou "poznámky", které přidáme do dokumentu, abychom označili informace nebo zvýraznili položky, které by je zajímaly, pro pozdější použití. Ačkoli psaní poznámek o tištěných dokumentech je snadné a běžné, schopnost přidávat osobní komentáře k elektronickým dokumentům je obvykle velmi omezená, pokud je vůbec k dispozici.  
  
 Toto téma popisuje několik běžných typů poznámek, konkrétně rychlé poznámky a zvýraznění, a ilustruje, jak rozhraní Microsoft Anotations Framework usnadňuje tyto typy poznámek v aplikacích prostřednictvím nadace Windows Presentation Foundation (WPF ) ovládací prvky pro zobrazení dokumentu.  WPF ovládací prvky zobrazení dokumentu, <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentScrollViewer>které podporují poznámky patří <xref:System.Windows.Controls.Primitives.DocumentViewerBase> a <xref:System.Windows.Controls.DocumentViewer> <xref:System.Windows.Controls.FlowDocumentPageViewer>, stejně jako ovládací prvky odvozené z například a .  

<a name="caf1_type_stickynotes"></a>
## <a name="sticky-notes"></a>Rychlé poznámky  
 Typická poznámka obsahuje informace napsané na malém kousku barevného papíru, který je pak "přilepená" na dokument. Digitální rychlé poznámky poskytují podobné funkce pro elektronické dokumenty, ale s větší flexibilitou zahrnout mnoho dalších typů obsahu, jako je například zadaný text, ručně psané poznámky (například tablet PC "inkoust" tahy) nebo webové odkazy.  
  
 Následující obrázek znázorňuje některé příklady poznámek poznámky zvýraznění, textové rychlé poznámky a poznámky rychlé poznámky.  
  
 ![Zvýrazňte poznámky s lepkavou poznámkou pro text a inkoust.](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Následující příklad ukazuje metodu, kterou můžete použít k povolení podpory poznámky ve vaší aplikaci.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>
## <a name="highlights"></a>Nejzajímavější body  
 Lidé používají kreativní metody, aby upozornili na zajímavé položky, když označí papírový dokument, jako je podtržení, zvýraznění, kroužení slov ve větě nebo kreslení značek nebo zápisů na okraji.  Zvýraznění poznámek v rozhraní Microsoft Anotations Framework poskytuje podobnou funkci pro označování informací zobrazených v ovládacích prvcích zobrazení dokumentů WPF.  
  
 Následující obrázek znázorňuje příklad zvýraznění poznámky.  
  
 ![Zvýraznění poznámky](./media/caf-callouts.png "CAF_Callouts")  
  
 Uživatelé obvykle vytvářejí poznámky tak, že nejprve vybere nějaký text nebo položku, která je předmětem zájmu, a potom klepnutím pravým tlačítkem myši zobrazíte možnosti <xref:System.Windows.Controls.ContextMenu> poznámky.  Následující příklad [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ukazuje, jak můžete <xref:System.Windows.Controls.ContextMenu> deklarovat příkazy s směrovcí, ke kterým mají uživatelé přístup k vytváření a správě anotací.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>
## <a name="data-anchoring"></a>Kotvení dat  
 Architektura anotací váže poznámky k datům, která uživatel vybere, nikoli pouze na pozici v zobrazení zobrazení. Proto pokud se změní zobrazení dokumentu, například když uživatel posouvá nebo mění velikost okna zobrazení, poznámky zůstane s výběrem dat, ke kterému je vázán. Například následující obrázek znázorňuje poznámku, kterou uživatel vytvořil při výběru textu. Když se zobrazení dokumentu změní (posune, změní velikost, změní velikost, změní velikost nebo se jinak přesune), zvýraznění se přesune s původním výběrem dat.  
  
 ![Ukotvení dat poznámky](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>
## <a name="matching-annotations-with-annotated-objects"></a>Porovnávání poznámk s objekty s poznámkami  
 Poznámky můžete porovnat s odpovídajícími objekty s anotací. Zvažte například jednoduchou aplikaci pro čtení dokumentů, která má podokno poznámek. Podokno poznámek může být seznam, který zobrazuje text ze seznamu poznámek ukotvených v dokumentu. Pokud uživatel vybere položku v seznamu, aplikace se zobrazí do zobrazení odstavce v dokumentu, ke kterému je odpovídající objekt poznámky ukotven.  
  
 Následující příklad ukazuje, jak implementovat obslužnou rutinu události takového seznamu, který slouží jako podokno poznámek.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Další příklad scénáře zahrnuje aplikace, které umožňují výměnu poznámek a rychlé poznámky mezi čtečkami dokumentů prostřednictvím e-mailu. Tato funkce umožňuje těmto aplikacím přejít čtenáře na stránku, která obsahuje poznámku, která je právě vyměňována.  
  
## <a name="see-also"></a>Viz také

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
- [Postup: Přidání příkazu do položky MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
