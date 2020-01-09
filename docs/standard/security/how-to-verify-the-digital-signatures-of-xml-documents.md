---
title: 'Postupy: Ověření digitálních podpisů dokumentů XML'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: 5d562c23d3b0fd7eda5dc273932ada77709641a1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706003"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Postupy: Ověření digitálních podpisů dokumentů XML
Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k ověření dat XML podepsaných digitálním podpisem. Digitální podpisy XML (XMLDSIG) umožňují ověřit, že data nebyla po podepsání změněna. Další informace o standardu XMLDSIG najdete v tématu Specifikace konsorcium World Wide Web (W3C) na <https://www.w3.org/TR/xmldsig-core/>.
  
 Příklad kódu v tomto postupu ukazuje, jak ověřit digitální podpis XML obsažený v <`Signature`> elementu.  Příklad načte veřejný klíč RSA z kontejneru klíčů a potom pomocí klíče ověří podpis.  
  
 Informace o tom, jak vytvořit digitální podpis, který lze ověřit pomocí této techniky, naleznete v tématu [How to: Sign XML Documents with digital signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Ověření digitálního podpisu dokumentu XML  
  
1. Chcete-li ověřit dokument, je nutné použít stejný asymetrický klíč, který byl použit k podepsání.  Vytvořte objekt <xref:System.Security.Cryptography.CspParameters> a zadejte název kontejneru klíčů, který se použil k podepsání.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Načtěte veřejný klíč pomocí třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Klíč je automaticky načten z kontejneru klíčů podle názvu při předání objektu <xref:System.Security.Cryptography.CspParameters> do konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.  Objekt <xref:System.Xml.XmlDocument> obsahuje podepsaný dokument XML, který se má ověřit.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Vytvořte nový objekt <xref:System.Security.Cryptography.Xml.SignedXml> a předejte mu objekt <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Vyhledejte prvek <`signature`> a vytvořte nový objekt <xref:System.Xml.XmlNodeList>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Načtěte XML prvního <`signature`> elementu do objektu <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Ověřte podpis pomocí metody <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> a veřejného klíče RSA.  Tato metoda vrací logickou hodnotu, která označuje úspěch nebo neúspěch.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.  Soubor `"test.xml"` musí být podepsán pomocí technik popsaných v tématu [Postupy: podepisování dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.  
  
- Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.  Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy nevkládat privátní klíč přímo do zdrojového kódu.  Vložené klíče lze snadno přečíst ze sestavení pomocí nástroje [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Podepisování dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
