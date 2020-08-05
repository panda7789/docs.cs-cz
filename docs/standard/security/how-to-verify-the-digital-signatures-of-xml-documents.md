---
title: 'Postupy: Ověření digitálních podpisů dokumentů XML'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSA class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: b9b2dc6a558d1fd6acd2922a7c8ad82ce8776c26
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557044"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Postupy: Ověření digitálních podpisů dokumentů XML

Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k ověření dat XML podepsaných digitálním podpisem. Digitální podpisy XML (XMLDSIG) umožňují ověřit, že data nebyla po podepsání změněna. Další informace o standardu XMLDSIG najdete v tématu Specifikace konsorcium World Wide Web (W3C) na adrese <https://www.w3.org/TR/xmldsig-core/> .
  
> [!NOTE]
> Kód v tomto článku se vztahuje na systém Windows.

Příklad kódu v tomto postupu ukazuje, jak ověřit digitální podpis XML obsažený v `Signature` prvku <>.  Příklad načte veřejný klíč RSA z kontejneru klíčů a potom pomocí klíče ověří podpis.  
  
Informace o tom, jak vytvořit digitální podpis, který lze ověřit pomocí této techniky, naleznete v tématu [How to: Sign XML Documents with digital signatures](how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Ověření digitálního podpisu dokumentu XML  
  
1. Chcete-li ověřit dokument, je nutné použít stejný asymetrický klíč, který byl použit k podepsání.  Vytvořte <xref:System.Security.Cryptography.CspParameters> objekt a zadejte název kontejneru klíčů, který se použil k podepsání.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Načtěte veřejný klíč pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Klíč je automaticky načten z kontejneru klíčů podle názvu při předání <xref:System.Security.Cryptography.CspParameters> objektu konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Vytvořte <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument>Objekt obsahuje podepsaný dokument XML, který se má ověřit.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Vytvoří nový <xref:System.Security.Cryptography.Xml.SignedXml> objekt a předá <xref:System.Xml.XmlDocument> ho objektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Vyhledejte prvek <`signature`> a vytvořte nový <xref:System.Xml.XmlNodeList> objekt.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Načtěte XML prvního <`signature`> elementu do <xref:System.Security.Cryptography.Xml.SignedXml> objektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Ověřte podpis pomocí <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> metody a veřejného klíče RSA.  Tato metoda vrací logickou hodnotu, která označuje úspěch nebo neúspěch.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Příklad

V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.  `"test.xml"`Soubor musí být podepsán pomocí technik popsaných v tématu [Postupy: podepisování dokumentů XML digitálními podpisy](how-to-sign-xml-documents-with-digital-signatures.md).  
  
[!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
[!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- V projektu, který cílí na .NET Framework, zahrňte odkaz na `System.Security.dll` .

- V projektu, který cílí na .NET Core nebo .NET 5, nainstalujte balíček NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).
  
- Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-security"></a>Zabezpečení .NET

Nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.  Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](generating-keys-for-encryption-and-decryption.md).  
  
Nikdy nevkládat privátní klíč přímo do zdrojového kódu.  Vložené klíče lze snadno přečíst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.  
  
## <a name="see-also"></a>Viz také

- [Kryptografický model](cryptography-model.md)
- [Šifrovací služby](cryptographic-services.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [Postupy: Podepisování dokumentů XML digitálními podpisy](how-to-sign-xml-documents-with-digital-signatures.md)
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
