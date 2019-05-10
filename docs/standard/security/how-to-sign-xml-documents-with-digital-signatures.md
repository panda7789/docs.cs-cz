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
ms.openlocfilehash: 0928f6091a80877609b545a25c8ac014f011d0b2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602608"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="89592-102">Postupy: Podepisování dokumentů XML digitálními podpisy</span><span class="sxs-lookup"><span data-stu-id="89592-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="89592-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů dokumentu XML nebo jeho část dokumentu XML s digitálním podpisem.</span><span class="sxs-lookup"><span data-stu-id="89592-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="89592-104">XML – digitální podpisy (XMLDSIG) umožňují ověřit, že data nebyla změněna po byla podepsána.</span><span class="sxs-lookup"><span data-stu-id="89592-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="89592-105">Další informace o standardních XMLDSIG, naleznete v tématu World Wide Web Consortium (W3C) doporučení [podpis syntaxe jazyka XML a zpracování](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="89592-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="89592-106">Příklad kódu v tomto postupu ukazuje, jak digitálně podepsat celý dokument XML a připojit k dokumentu v podpis <`Signature`> element.</span><span class="sxs-lookup"><span data-stu-id="89592-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="89592-107">V příkladu vytvoří podpisový klíč RSA, přidá klíč do zabezpečeného kontejneru klíčů a potom pomocí klíče k digitálnímu podepisování dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="89592-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="89592-108">Klíč je pak načíst do ověření digitálního podpisu XML nebo můžete použít k podepsání jiného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="89592-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="89592-109">Informace o tom, jak ověřit digitální podpis XML, který byl vytvořen pomocí tohoto postupu najdete v tématu [jak: Ověření digitálních podpisů dokumentů XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="89592-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="89592-110">K digitálnímu podepisování dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="89592-110">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="89592-111">Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="89592-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="89592-112">Generovat objekt asymetrického klíče pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="89592-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="89592-113">Klíč se automaticky uloží do kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="89592-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="89592-114">Tento klíč se používá k podepisování dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="89592-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="89592-115">Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="89592-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="89592-116"><xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.</span><span class="sxs-lookup"><span data-stu-id="89592-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="89592-117">Vytvořte nový <xref:System.Security.Cryptography.Xml.SignedXml> objektu a předejte <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="89592-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="89592-118">Přidat podpisový klíč RSA k <xref:System.Security.Cryptography.Xml.SignedXml> objektu.</span><span class="sxs-lookup"><span data-stu-id="89592-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="89592-119">Vytvoření <xref:System.Security.Cryptography.Xml.Reference> objekt, který popisuje, co k podepsání.</span><span class="sxs-lookup"><span data-stu-id="89592-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="89592-120">Pro přihlášení v celém dokumentu, nastavte <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> vlastnost `""`.</span><span class="sxs-lookup"><span data-stu-id="89592-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="89592-121">Přidat <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> objektu <xref:System.Security.Cryptography.Xml.Reference> objektu.</span><span class="sxs-lookup"><span data-stu-id="89592-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="89592-122">Transformace umožňuje verifier ke znázornění dat XML identické způsobem, který používá podpisu.</span><span class="sxs-lookup"><span data-stu-id="89592-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="89592-123">XML data lze reprezentovat různými způsoby, abyste tento krok je důležité k ověření.</span><span class="sxs-lookup"><span data-stu-id="89592-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="89592-124">Přidat <xref:System.Security.Cryptography.Xml.Reference> objektu <xref:System.Security.Cryptography.Xml.SignedXml> objektu.</span><span class="sxs-lookup"><span data-stu-id="89592-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="89592-125">Vypočítat podpis voláním <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="89592-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="89592-126">Načíst reprezentaci XML pro podpis (<`Signature`> element) a uložte ho do nového <xref:System.Xml.XmlElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="89592-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="89592-127">Přidat element do <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="89592-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="89592-128">Uložte dokument.</span><span class="sxs-lookup"><span data-stu-id="89592-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="89592-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="89592-129">Example</span></span>  
 <span data-ttu-id="89592-130">Tento příklad předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="89592-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="89592-131">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="89592-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="89592-132">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="89592-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="89592-133">Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="89592-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="89592-134">Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="89592-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="89592-135">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="89592-135">.NET Framework Security</span></span>  
 <span data-ttu-id="89592-136">Nikdy ukládat nebo přenášet privátní klíč pro pár asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="89592-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="89592-137">Další informace o symetrický a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="89592-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="89592-138">Nikdy vložení privátního klíče přímo do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="89592-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="89592-139">Vložené klíče ze sestavení pomocí snadno přečíst [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je například Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="89592-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89592-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89592-140">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="89592-141">Postupy: Ověření digitálních podpisů dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="89592-141">How to: Verify the Digital Signatures of XML Documents</span></span>](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
