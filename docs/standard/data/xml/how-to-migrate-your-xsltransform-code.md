---
title: "Postupy: migrace kódu XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f8a9e287e611e1cb1731c267702504637b23081b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Postupy: migrace kódu XslTransform
Nové třídy XSLT byly navrženy pro velmi podobný existujících tříd. <xref:System.Xml.Xsl.XslCompiledTransform> Třídy nahradí <xref:System.Xml.Xsl.XslTransform> třídy. Šablony stylů kompilované pomocí <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda. Transformace jsou spouštěny pomocí <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda. Následující postupy ukazují běžné úlohy XSLT a porovnání kódu pomocí <xref:System.Xml.Xsl.XslTransform> třídy <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>K transformaci souboru a výstup k identifikátoru URI  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Pro kompilaci šablony stylů a překladač pomocí výchozích pověření  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>Použití parametru XSLT  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>Chcete-li povolit skriptování XSLT  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Načíst výsledky do objektu modelu DOM  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
    > [!NOTE]
    >  <xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá metodu, která vrátí výsledky transformace XSLT jako <xref:System.Xml.XmlReader> objektu. Však můžete výstup do souboru XML a načíst soubor XML do jiného objektu.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>K vysílání datového proudu výsledky do jiného úložiště dat  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
-   Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Viz také  
 [Migrace z XslTransform – třída](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
