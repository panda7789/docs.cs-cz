---
title: 'Postupy: Dešifrování elementů XML pomocí asymetrických klíčů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 5ed1e2eb2518366da0a57655d7a8691e23f725d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706133"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="af063-102">Postupy: Dešifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="af063-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="af063-103">Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování a dešifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="af063-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="af063-104">Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="af063-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="af063-105">Další informace o standardu šifrování XML najdete v tématu [syntaxe a zpracování signatur XML](https://www.w3.org/TR/xmldsig-core/)doporučení pro konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="af063-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="af063-106">Příklad v tomto postupu dešifruje XML element, který byl zašifrován pomocí metod popsaných v tématu [Postupy: šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="af063-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="af063-107">Najde <`EncryptedData`> element, dešifruje prvek a pak nahradí element původním nešifrovaným XML elementem.</span><span class="sxs-lookup"><span data-stu-id="af063-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="af063-108">Tento příklad dešifruje XML element pomocí dvou klíčů.</span><span class="sxs-lookup"><span data-stu-id="af063-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="af063-109">Načte dříve vygenerovaný privátní klíč RSA z kontejneru klíčů a potom pomocí klíče RSA dešifruje klíč relace uložený ve <`EncryptedKey`> elementu <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="af063-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="af063-110">Příklad poté používá klíč relace k dešifrování XML elementu.</span><span class="sxs-lookup"><span data-stu-id="af063-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="af063-111">Tento příklad je vhodný pro situace, kdy více aplikací musí sdílet šifrovaná data nebo kde aplikace musí ukládat šifrovaná data mezi časy, ve kterých je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="af063-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="af063-112">Dešifrování elementu XML pomocí asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="af063-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="af063-113">Vytvořte objekt <xref:System.Security.Cryptography.CspParameters> a zadejte název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="af063-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="af063-114">Načte dříve generovaný asymetrický klíč z kontejneru pomocí objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="af063-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="af063-115">Klíč je automaticky načten z kontejneru klíčů při předání objektu <xref:System.Security.Cryptography.CspParameters> do konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="af063-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="af063-116">Vytvořte nový objekt <xref:System.Security.Cryptography.Xml.EncryptedXml> k dešifrování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="af063-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="af063-117">Přidejte mapování klíč/název pro přidružení klíče RSA k elementu v dokumentu, který má být dešifrován.</span><span class="sxs-lookup"><span data-stu-id="af063-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="af063-118">Pro klíč, který jste použili při šifrování dokumentu, je nutné použít stejný název.</span><span class="sxs-lookup"><span data-stu-id="af063-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="af063-119">Všimněte si, že tento název je oddělený od názvu používaného k identifikaci klíče v kontejneru klíčů zadaného v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="af063-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="af063-120">Zavolejte metodu <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> pro dešifrování <`EncryptedData`elementu >.</span><span class="sxs-lookup"><span data-stu-id="af063-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="af063-121">Tato metoda používá klíč RSA k dešifrování klíče relace a automaticky používá klíč relace k dešifrování XML elementu.</span><span class="sxs-lookup"><span data-stu-id="af063-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="af063-122">Také automaticky nahradí <`EncryptedData`> prvek původním prostým textem.</span><span class="sxs-lookup"><span data-stu-id="af063-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="af063-123">Uložte dokument XML.</span><span class="sxs-lookup"><span data-stu-id="af063-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="af063-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="af063-124">Example</span></span>  
 <span data-ttu-id="af063-125">V tomto příkladu se předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="af063-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="af063-126">Předpokládá také, že `test.xml` obsahuje XML element, který byl zašifrován pomocí metod popsaných v tématu [How to: ENCRYPT XML Elements with asymetrické klíče](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="af063-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="af063-127">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="af063-127">Compiling the Code</span></span>  
  
- <span data-ttu-id="af063-128">Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="af063-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="af063-129">Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="af063-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="af063-130">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="af063-130">.NET Framework Security</span></span>  
 <span data-ttu-id="af063-131">Nikdy neukládejte symetrický kryptografický klíč ve formě prostého textu nebo přenášet symetrický klíč mezi počítači ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="af063-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="af063-132">Kromě toho nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="af063-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="af063-133">Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="af063-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="af063-134">Nikdy nevkládat klíč přímo do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="af063-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="af063-135">Vložené klíče lze snadno přečíst ze sestavení pomocí [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="af063-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="af063-136">Až budete s použitím kryptografického klíče hotovi, vymažte ho z paměti nastavením každého bajtu na nulu nebo voláním metody <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="af063-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="af063-137">Kryptografické klíče je někdy možné z paměti načítat pomocí ladicího programu nebo je číst z pevného disku, pokud je umístění v paměti stránkované na disk.</span><span class="sxs-lookup"><span data-stu-id="af063-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af063-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af063-138">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="af063-139">Postupy: Šifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="af063-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
