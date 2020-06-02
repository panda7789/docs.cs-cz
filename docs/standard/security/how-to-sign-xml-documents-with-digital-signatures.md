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
ms.openlocfilehash: 81fa5e4c503f26dc13758090f845fd8387287084
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277177"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="9dce4-102">Postupy: Podepisování dokumentů XML digitálními podpisy</span><span class="sxs-lookup"><span data-stu-id="9dce4-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="9dce4-103">Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k podepsání dokumentu XML nebo části dokumentu XML s digitálním podpisem.</span><span class="sxs-lookup"><span data-stu-id="9dce4-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="9dce4-104">Digitální podpisy XML (XMLDSIG) umožňují ověřit, že data nebyla po podepsání změněna.</span><span class="sxs-lookup"><span data-stu-id="9dce4-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="9dce4-105">Další informace o standardu XMLDSIG najdete v tématu [syntaxe a zpracování signatur XML](https://www.w3.org/TR/xmldsig-core/)doporučení pro konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="9dce4-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="9dce4-106">Příklad kódu v tomto postupu ukazuje, jak digitálně podepsat celý dokument XML a připojit podpis k dokumentu v `Signature` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="9dce4-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="9dce4-107">Příklad vytvoří podpisový klíč RSA, přidá klíč do zabezpečeného kontejneru klíčů a potom použije klíč k digitálnímu podepsání dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9dce4-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="9dce4-108">Klíč lze poté načíst pro ověření digitálního podpisu XML nebo lze použít k podepsání jiného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9dce4-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="9dce4-109">Informace o tom, jak ověřit digitální podpis XML, který byl vytvořen pomocí tohoto postupu, naleznete v tématu [How to: Verify Digital Signatures XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="9dce4-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="9dce4-110">Chcete-li digitálně podepsat dokument XML</span><span class="sxs-lookup"><span data-stu-id="9dce4-110">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="9dce4-111">Vytvořte <xref:System.Security.Cryptography.CspParameters> objekt a zadejte název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="9dce4-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="9dce4-112">Vygenerujte asymetrický klíč pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="9dce4-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="9dce4-113">Klíč se automaticky uloží do kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> objektu konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="9dce4-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="9dce4-114">Tento klíč bude použit k podepsání dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9dce4-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="9dce4-115">Vytvořte <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="9dce4-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="9dce4-116"><xref:System.Xml.XmlDocument>Objekt obsahuje element XML k zašifrování.</span><span class="sxs-lookup"><span data-stu-id="9dce4-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="9dce4-117">Vytvoří nový <xref:System.Security.Cryptography.Xml.SignedXml> objekt a předá <xref:System.Xml.XmlDocument> ho objektu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="9dce4-118">Přidejte podpisový klíč RSA do <xref:System.Security.Cryptography.Xml.SignedXml> objektu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="9dce4-119">Vytvořte <xref:System.Security.Cryptography.Xml.Reference> objekt, který popisuje, co se má podepsat.</span><span class="sxs-lookup"><span data-stu-id="9dce4-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="9dce4-120">Pro podepsání celého dokumentu nastavte <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> vlastnost na hodnotu `""` .</span><span class="sxs-lookup"><span data-stu-id="9dce4-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="9dce4-121">Přidejte <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> objekt do <xref:System.Security.Cryptography.Xml.Reference> objektu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="9dce4-122">Transformace umožňuje ověřovateli reprezentovat XML data identickým způsobem, který používá podepisující osoba.</span><span class="sxs-lookup"><span data-stu-id="9dce4-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="9dce4-123">Data XML lze reprezentovat různými způsoby, proto je tento krok nezbytný pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="9dce4-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="9dce4-124">Přidejte <xref:System.Security.Cryptography.Xml.Reference> objekt do <xref:System.Security.Cryptography.Xml.SignedXml> objektu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="9dce4-125">Vypočítá podpis voláním <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9dce4-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="9dce4-126">Načtěte reprezentace XML signatury (<`Signature`> element) a uložte ji do nového <xref:System.Xml.XmlElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="9dce4-127">Přidejte element k <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="9dce4-128">Uložte dokument.</span><span class="sxs-lookup"><span data-stu-id="9dce4-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="9dce4-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="9dce4-129">Example</span></span>  
 <span data-ttu-id="9dce4-130">V tomto příkladu se předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="9dce4-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="9dce4-131">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9dce4-132">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9dce4-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="9dce4-133">Chcete-li tento příklad zkompilovat, je nutné zahrnout odkaz na `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="9dce4-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="9dce4-134">Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="9dce4-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9dce4-135">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9dce4-135">.NET Framework Security</span></span>  
 <span data-ttu-id="9dce4-136">Nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="9dce4-137">Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="9dce4-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="9dce4-138">Nikdy nevkládat privátní klíč přímo do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="9dce4-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="9dce4-139">Vložené klíče lze snadno přečíst ze sestavení pomocí nástroje [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="9dce4-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dce4-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="9dce4-140">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="9dce4-141">Postupy: Ověření digitálních podpisů dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="9dce4-141">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
