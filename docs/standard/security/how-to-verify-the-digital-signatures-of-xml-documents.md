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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ec813e50bb4dca33c8dda8b41914cfa5d5596c2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45593241"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Postupy: Ověření digitálních podpisů dokumentů XML
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro ověření dat XML podepsané digitálním podpisem.  XML – digitální podpisy (XMLDSIG) umožňují ověřit, že data nebyla změněna po byla podepsána.  Další informace o standardních XMLDSIG, naleznete v tématu Specifikace World Wide Web Consortium (W3C) na http://www.w3.org/TR/xmldsig-core/.  
  
 V tomto postupu příklad kódu ukazuje, jak ověřit digitální podpis XML obsažených v <`Signature`> element.  Příklad načte veřejný klíč RSA v kontejneru klíčů a potom použije klíč k ověření podpisu.  
  
 Informace, jak vytvořit digitální podpis, který se dá ověřit pomocí této techniky, naleznete v tématu [postupy: přihlášení dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Chcete-li ověřit digitální podpis dokumentu XML  
  
1.  K ověření dokumentu, musíte použít stejné asymetrický klíč, který byl použit pro podepisování.  Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů, který byl použit pro podepisování.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Načíst veřejný klíč pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Klíč je automaticky načtena z kontejneru klíčů podle názvu při předání <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje podepsaný dokument XML k ověření.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Vytvořte nový <xref:System.Security.Cryptography.Xml.SignedXml> objektu a předejte <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Najít <`signature`> element a vytvořte nový <xref:System.Xml.XmlNodeList> objektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  Načtení XML první <`signature`> elementu do <xref:System.Security.Cryptography.Xml.SignedXml> objektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Kontrola podpisu pomocí <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> metoda a veřejný klíč RSA.  Tato metoda vrátí logickou hodnotu, která indikuje úspěch nebo neúspěch.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Příklad  
 Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.  `"test.xml"` Souboru musí být podepsané pomocí technik popsaných v [postupy: přihlášení dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.  
  
-   Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy ukládat nebo přenášet privátní klíč pro pár asymetrických klíčů ve formátu prostého textu.  Další informace o symetrický a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy vložení privátního klíče přímo do zdrojového kódu.  Vložené klíče ze sestavení pomocí snadno přečíst [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je například Poznámkový blok.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>  
- [Postupy: Podepisování dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
