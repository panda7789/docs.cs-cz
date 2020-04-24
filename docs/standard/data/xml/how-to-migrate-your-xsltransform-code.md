---
title: 'Postupy: Migrace kódu XslTransform'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 2bc5cbc1b0857a82d3b0a11f05a4eb5756724546
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710840"
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Postupy: Migrace kódu XslTransform
Nové třídy XSLT byly navrženy tak, aby byly velmi podobné existujícím třídám. <xref:System.Xml.Xsl.XslCompiledTransform> Třída nahrazuje <xref:System.Xml.Xsl.XslTransform> třídu. Šablony stylů jsou kompilovány pomocí <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Transformace jsou spouštěny pomocí <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Následující postupy ukazují běžné úlohy XSLT a porovnávají kód pomocí <xref:System.Xml.Xsl.XslTransform> třídy versus <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Transformace souboru a výstupu na identifikátor URI  
  
- Kód pomocí <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- Kód pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Kompilace šablon stylů a použití překladače s výchozími přihlašovacími údaji  
  
- Kód pomocí <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- Kód pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>Použití parametru XSLT  
  
- Kód pomocí <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- Kód pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>Povolení skriptování XSLT  
  
- Kód pomocí <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- Kód pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Načtení výsledků do objektu modelu DOM  
  
- Kód pomocí <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- Kód pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
    > [!NOTE]
    > <xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá metodu, která vrátí výsledky transformace XSLT jako <xref:System.Xml.XmlReader> objekt. Můžete však výstup do souboru XML a načíst soubor XML do jiného objektu.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Postup streamování výsledků do jiného úložiště dat  
  
- Kód pomocí <xref:System.Xml.Xsl.XslTransform> třídy.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- Kód pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Viz také

- [Migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
