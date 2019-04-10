---
title: 'Postupy: Podepisování dokumentů XML digitálními podpisy'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39e053ea9ca0b2fdc548a4b9447d34e852816a61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324497"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>Postupy: Podepisování dokumentů XML digitálními podpisy
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů dokumentu XML nebo jeho část dokumentu XML s digitálním podpisem.  XML – digitální podpisy (XMLDSIG) umožňují ověřit, že data nebyla změněna po byla podepsána.  Další informace o standardních XMLDSIG, naleznete v tématu World Wide Web Consortium (W3C) doporučení [podpis syntaxe jazyka XML a zpracování](https://www.w3.org/TR/xmldsig-core/).  
  
 Příklad kódu v tomto postupu ukazuje, jak digitálně podepsat celý dokument XML a připojit k dokumentu v podpis <`Signature`> element.  V příkladu vytvoří podpisový klíč RSA, přidá klíč do zabezpečeného kontejneru klíčů a potom pomocí klíče k digitálnímu podepisování dokumentu XML.  Klíč je pak načíst do ověření digitálního podpisu XML nebo můžete použít k podepsání jiného dokumentu XML.  
  
 Informace o tom, jak ověřit digitální podpis XML, který byl vytvořen pomocí tohoto postupu najdete v tématu [jak: Ověření digitálních podpisů dokumentů XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).  
  
### <a name="to-digitally-sign-an-xml-document"></a>K digitálnímu podepisování dokumentu XML  
  
1. Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Generovat objekt asymetrického klíče pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Klíč se automaticky uloží do kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Tento klíč se používá k podepisování dokumentů XML.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Vytvořte nový <xref:System.Security.Cryptography.Xml.SignedXml> objektu a předejte <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Přidat podpisový klíč RSA k <xref:System.Security.Cryptography.Xml.SignedXml> objektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Vytvoření <xref:System.Security.Cryptography.Xml.Reference> objekt, který popisuje, co k podepsání.  Pro přihlášení v celém dokumentu, nastavte <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> vlastnost `""`.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Přidat <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> objektu <xref:System.Security.Cryptography.Xml.Reference> objektu.  Transformace umožňuje verifier ke znázornění dat XML identické způsobem, který používá podpisu.  XML data lze reprezentovat různými způsoby, abyste tento krok je důležité k ověření.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. Přidat <xref:System.Security.Cryptography.Xml.Reference> objektu <xref:System.Security.Cryptography.Xml.SignedXml> objektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. Vypočítat podpis voláním <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> metody.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. Načíst reprezentaci XML pro podpis (<`Signature`> element) a uložte ho do nového <xref:System.Xml.XmlElement> objektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. Přidat element do <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. Uložte dokument.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>Příklad  
 Tento příklad předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako zkompilovaný program.  Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.  
  
-   Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy ukládat nebo přenášet privátní klíč pro pár asymetrických klíčů ve formátu prostého textu.  Další informace o symetrický a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy vložení privátního klíče přímo do zdrojového kódu.  Vložené klíče ze sestavení pomocí snadno přečíst [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je například Poznámkový blok.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Ověření digitálních podpisů dokumentů XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
