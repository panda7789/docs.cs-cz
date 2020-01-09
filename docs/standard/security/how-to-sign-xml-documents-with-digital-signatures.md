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
ms.openlocfilehash: 0df036b3336527f3cc0e48d9a7ec835ab9f1cf4a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706042"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>Postupy: Podepisování dokumentů XML digitálními podpisy
Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> pro podepsání dokumentu XML nebo části dokumentu XML s digitálním podpisem.  Digitální podpisy XML (XMLDSIG) umožňují ověřit, že data nebyla po podepsání změněna.  Další informace o standardu XMLDSIG najdete v tématu [syntaxe a zpracování signatur XML](https://www.w3.org/TR/xmldsig-core/)doporučení pro konsorcium World Wide Web (W3C).  
  
 Příklad kódu v tomto postupu ukazuje, jak digitálně podepsat celý dokument XML a jak tento podpis připojit k dokumentu v <`Signature`> elementu.  Příklad vytvoří podpisový klíč RSA, přidá klíč do zabezpečeného kontejneru klíčů a potom použije klíč k digitálnímu podepsání dokumentu XML.  Klíč lze poté načíst pro ověření digitálního podpisu XML nebo lze použít k podepsání jiného dokumentu XML.  
  
 Informace o tom, jak ověřit digitální podpis XML, který byl vytvořen pomocí tohoto postupu, naleznete v tématu [How to: Verify Digital Signatures XML Documents](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).  
  
### <a name="to-digitally-sign-an-xml-document"></a>Chcete-li digitálně podepsat dokument XML  
  
1. Vytvořte objekt <xref:System.Security.Cryptography.CspParameters> a zadejte název kontejneru klíčů.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Vygenerujte asymetrický klíč pomocí třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Klíč se automaticky uloží do kontejneru klíčů při předání objektu <xref:System.Security.Cryptography.CspParameters> do konstruktoru třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Tento klíč bude použit k podepsání dokumentu XML.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.  Objekt <xref:System.Xml.XmlDocument> obsahuje element XML k zašifrování.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Vytvořte nový objekt <xref:System.Security.Cryptography.Xml.SignedXml> a předejte mu objekt <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Přidejte podpisový klíč RSA do objektu <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Vytvořte objekt <xref:System.Security.Cryptography.Xml.Reference>, který popisuje, co se má podepsat.  Pro podepsání celého dokumentu nastavte vlastnost <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> na hodnotu `""`.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Přidejte objekt <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> do objektu <xref:System.Security.Cryptography.Xml.Reference>.  Transformace umožňuje ověřovateli reprezentovat XML data identickým způsobem, který používá podepisující osoba.  Data XML lze reprezentovat různými způsoby, proto je tento krok nezbytný pro ověřování.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. Přidejte objekt <xref:System.Security.Cryptography.Xml.Reference> do objektu <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. Vypočítá podpis voláním metody <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. Načtěte reprezentace XML signatury (<`Signature`> elementu) a uložte ji do nového objektu <xref:System.Xml.XmlElement>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. Přidejte element do objektu <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. Uložte dokument.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako kompilovaný program.  Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.  
  
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
  
- Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.  
  
- Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.  Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy nevkládat privátní klíč přímo do zdrojového kódu.  Vložené klíče lze snadno přečíst ze sestavení pomocí nástroje [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Ověření digitálních podpisů dokumentů XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
