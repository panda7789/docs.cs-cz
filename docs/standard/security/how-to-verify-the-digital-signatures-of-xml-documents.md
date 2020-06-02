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
ms.openlocfilehash: fa5e13e4a84a7d5d5c07c63df9079f4a07aebc62
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277138"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="59477-102">Postupy: Ověření digitálních podpisů dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="59477-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="59477-103">Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k ověření dat XML podepsaných digitálním podpisem.</span><span class="sxs-lookup"><span data-stu-id="59477-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="59477-104">Digitální podpisy XML (XMLDSIG) umožňují ověřit, že data nebyla po podepsání změněna.</span><span class="sxs-lookup"><span data-stu-id="59477-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="59477-105">Další informace o standardu XMLDSIG najdete v tématu Specifikace konsorcium World Wide Web (W3C) na adrese <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="59477-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
 <span data-ttu-id="59477-106">Příklad kódu v tomto postupu ukazuje, jak ověřit digitální podpis XML obsažený v `Signature` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="59477-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="59477-107">Příklad načte veřejný klíč RSA z kontejneru klíčů a potom pomocí klíče ověří podpis.</span><span class="sxs-lookup"><span data-stu-id="59477-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="59477-108">Informace o tom, jak vytvořit digitální podpis, který lze ověřit pomocí této techniky, naleznete v tématu [How to: Sign XML Documents with digital signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="59477-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="59477-109">Ověření digitálního podpisu dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="59477-109">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="59477-110">Chcete-li ověřit dokument, je nutné použít stejný asymetrický klíč, který byl použit k podepsání.</span><span class="sxs-lookup"><span data-stu-id="59477-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="59477-111">Vytvořte <xref:System.Security.Cryptography.CspParameters> objekt a zadejte název kontejneru klíčů, který se použil k podepsání.</span><span class="sxs-lookup"><span data-stu-id="59477-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="59477-112">Načtěte veřejný klíč pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="59477-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="59477-113">Klíč je automaticky načten z kontejneru klíčů podle názvu při předání <xref:System.Security.Cryptography.CspParameters> objektu konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="59477-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="59477-114">Vytvořte <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="59477-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="59477-115"><xref:System.Xml.XmlDocument>Objekt obsahuje podepsaný dokument XML, který se má ověřit.</span><span class="sxs-lookup"><span data-stu-id="59477-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="59477-116">Vytvoří nový <xref:System.Security.Cryptography.Xml.SignedXml> objekt a předá <xref:System.Xml.XmlDocument> ho objektu.</span><span class="sxs-lookup"><span data-stu-id="59477-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="59477-117">Vyhledejte prvek <`signature`> a vytvořte nový <xref:System.Xml.XmlNodeList> objekt.</span><span class="sxs-lookup"><span data-stu-id="59477-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="59477-118">Načtěte XML prvního <`signature`> elementu do <xref:System.Security.Cryptography.Xml.SignedXml> objektu.</span><span class="sxs-lookup"><span data-stu-id="59477-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="59477-119">Ověřte podpis pomocí <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> metody a veřejného klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="59477-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="59477-120">Tato metoda vrací logickou hodnotu, která označuje úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="59477-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="59477-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="59477-121">Example</span></span>  
 <span data-ttu-id="59477-122">V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="59477-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="59477-123">`"test.xml"`Soubor musí být podepsán pomocí technik popsaných v tématu [Postupy: podepisování dokumentů XML digitálními podpisy](how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="59477-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59477-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="59477-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="59477-125">Chcete-li tento příklad zkompilovat, je nutné zahrnout odkaz na `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="59477-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="59477-126">Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="59477-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="59477-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59477-127">.NET Framework Security</span></span>  
 <span data-ttu-id="59477-128">Nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="59477-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="59477-129">Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="59477-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="59477-130">Nikdy nevkládat privátní klíč přímo do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="59477-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="59477-131">Vložené klíče lze snadno přečíst ze sestavení pomocí nástroje [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="59477-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59477-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="59477-132">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="59477-133">Postupy: Podepisování dokumentů XML digitálními podpisy</span><span class="sxs-lookup"><span data-stu-id="59477-133">How to: Sign XML Documents with Digital Signatures</span></span>](how-to-sign-xml-documents-with-digital-signatures.md)
