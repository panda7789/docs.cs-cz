---
title: "Postupy: Ověření digitálních podpisů dokumentů XML"
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
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c45ffbffd5eae812dbd9703ffde4423c94581234
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Postupy: Ověření digitálních podpisů dokumentů XML
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro ověření dat XML podepsané digitální podpis.  XML – digitální podpisy (XMLDSIG) umožňují ověřte, že data nebyla změněna po podepsání.  Další informace o standardu XMLDSIG naleznete ve specifikaci World Wide Web Consortium (W3C) na http://www.w3.org/TR/xmldsig-core/.  
  
 Příklad kódu v tomto postupu ukazuje, jak ověřit digitální podpis XML součástí <`Signature`> elementu.  V příkladu načte veřejný klíč RSA z kontejneru klíčů a pak používá klíč k ověření podpisu.  
  
 Informace, jak vytvořit digitální podpis, který lze ověřit pomocí Tato technika, naleznete v tématu [postupy: přihlášení dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Chcete-li ověřit digitální podpis dokumentu XML  
  
1.  Pokud chcete ověřit dokumentu, musíte použít stejné asymetrický klíč, který byl použit pro podepisování.  Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů, který byl použit pro podepisování.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Načíst veřejného klíče pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Klíč je automaticky načten z kontejneru klíčů podle názvu při předání <xref:System.Security.Cryptography.CspParameters> objektu do konstruktoru objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objektu obsahuje podepsaný dokument XML k ověření.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Vytvořte novou <xref:System.Security.Cryptography.Xml.SignedXml> objektu a předat <xref:System.Xml.XmlDocument> objektu k němu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Najít <`signature`> elementu a vytvořte novou <xref:System.Xml.XmlNodeList> objektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  Načtení XML prvního <`signature`> element do <xref:System.Security.Cryptography.Xml.SignedXml> objektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Zkontrolujte podpis pomocí <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> metoda a veřejným klíčem RSA.  Tato metoda vrací logickou hodnotu, která označuje úspěch nebo neúspěch.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Příklad  
 Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.  `"test.xml"` Souboru musí být podepsané pomocí technik popsaných v [postupy: přihlášení dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.  
  
-   Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy uložení nebo přeneste privátní klíč pár asymetrických klíčů ve formátu prostého textu.  Další informace o symetrické a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy vložení privátního klíče přímo do vašeho zdrojového kódu.  Vložené klíče lze snadno přečíst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, například Poznámkový blok.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography.Xml>  
 [Postupy: Podepisování dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
