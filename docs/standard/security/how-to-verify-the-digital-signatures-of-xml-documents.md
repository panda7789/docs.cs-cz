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
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="de330-102">Postupy: Ověření digitálních podpisů dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="de330-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="de330-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro ověření dat XML podepsané digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="de330-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span>  <span data-ttu-id="de330-104">XML – digitální podpisy (XMLDSIG) umožňují ověřte, že data nebyla změněna po podepsání.</span><span class="sxs-lookup"><span data-stu-id="de330-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="de330-105">Další informace o standardu XMLDSIG naleznete ve specifikaci World Wide Web Consortium (W3C) na http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="de330-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="de330-106">Příklad kódu v tomto postupu ukazuje, jak ověřit digitální podpis XML součástí <`Signature`> elementu.</span><span class="sxs-lookup"><span data-stu-id="de330-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="de330-107">V příkladu načte veřejný klíč RSA z kontejneru klíčů a pak používá klíč k ověření podpisu.</span><span class="sxs-lookup"><span data-stu-id="de330-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="de330-108">Informace, jak vytvořit digitální podpis, který lze ověřit pomocí Tato technika, naleznete v tématu [postupy: přihlášení dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="de330-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="de330-109">Chcete-li ověřit digitální podpis dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="de330-109">To verify the digital signature of an XML document</span></span>  
  
1.  <span data-ttu-id="de330-110">Pokud chcete ověřit dokumentu, musíte použít stejné asymetrický klíč, který byl použit pro podepisování.</span><span class="sxs-lookup"><span data-stu-id="de330-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="de330-111">Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů, který byl použit pro podepisování.</span><span class="sxs-lookup"><span data-stu-id="de330-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="de330-112">Načíst veřejného klíče pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="de330-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="de330-113">Klíč je automaticky načten z kontejneru klíčů podle názvu při předání <xref:System.Security.Cryptography.CspParameters> objektu do konstruktoru objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="de330-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="de330-114">Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="de330-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="de330-115"><xref:System.Xml.XmlDocument> Objektu obsahuje podepsaný dokument XML k ověření.</span><span class="sxs-lookup"><span data-stu-id="de330-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="de330-116">Vytvořte novou <xref:System.Security.Cryptography.Xml.SignedXml> objektu a předat <xref:System.Xml.XmlDocument> objektu k němu.</span><span class="sxs-lookup"><span data-stu-id="de330-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="de330-117">Najít <`signature`> elementu a vytvořte novou <xref:System.Xml.XmlNodeList> objektu.</span><span class="sxs-lookup"><span data-stu-id="de330-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="de330-118">Načtení XML prvního <`signature`> element do <xref:System.Security.Cryptography.Xml.SignedXml> objektu.</span><span class="sxs-lookup"><span data-stu-id="de330-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="de330-119">Zkontrolujte podpis pomocí <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> metoda a veřejným klíčem RSA.</span><span class="sxs-lookup"><span data-stu-id="de330-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="de330-120">Tato metoda vrací logickou hodnotu, která označuje úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="de330-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="de330-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="de330-121">Example</span></span>  
 <span data-ttu-id="de330-122">Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="de330-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="de330-123">`"test.xml"` Souboru musí být podepsané pomocí technik popsaných v [postupy: přihlášení dokumentů XML digitálními podpisy](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="de330-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de330-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="de330-124">Compiling the Code</span></span>  
  
-   <span data-ttu-id="de330-125">Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="de330-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="de330-126">Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="de330-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="de330-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="de330-127">.NET Framework Security</span></span>  
 <span data-ttu-id="de330-128">Nikdy uložení nebo přeneste privátní klíč pár asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="de330-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="de330-129">Další informace o symetrické a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="de330-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="de330-130">Nikdy vložení privátního klíče přímo do vašeho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="de330-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="de330-131">Vložené klíče lze snadno přečíst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, například Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="de330-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de330-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="de330-132">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="de330-133">Postupy: Podepisování dokumentů XML digitálními podpisy</span><span class="sxs-lookup"><span data-stu-id="de330-133">How to: Sign XML Documents with Digital Signatures</span></span>](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
