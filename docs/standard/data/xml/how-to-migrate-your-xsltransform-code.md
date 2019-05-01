---
title: 'Postupy: Migrace kódu XslTransform'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb8754c4e572464f139a6b072ccd542b1a302652
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027235"
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Postupy: Migrace kódu XslTransform
Byly navrženy nové třídy XSLT se velmi podobá existující třídy. <xref:System.Xml.Xsl.XslCompiledTransform> Třídy nahradí <xref:System.Xml.Xsl.XslTransform> třídy. Šablony stylů jsou kompilovány pomocí <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Transformace jsou spouštěny <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Následující postupy ukazují běžné úkoly XSLT a porovnejte kód s využitím <xref:System.Xml.Xsl.XslTransform> třídy a <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Transformace souboru a výstup do identifikátoru URI  
  
- Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Ke kompilaci šablony stylů a překladač pomocí výchozích přihlašovacích údajů  
  
- Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>Chcete-li použít parametr XSLT  
  
- Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>Povolit skriptování XSLT  
  
- Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Načíst výsledky do objektu modelu DOM  
  
- Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
    > [!NOTE]
    >  <xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá metodu, která vrátí výsledky transformace XSLT jako <xref:System.Xml.XmlReader> objektu. Můžete však výstup do souboru XML a načíst soubor XML do jiného objektu.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Abyste mohli Streamovat výsledky do jiného úložiště dat  
  
- Programování s využitím <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- Programování s využitím <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Viz také:

- [Migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
