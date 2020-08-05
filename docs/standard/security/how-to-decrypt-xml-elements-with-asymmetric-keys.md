---
title: 'Postupy: Dešifrování elementů XML pomocí asymetrických klíčů'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 4a06628ddde0920133bfd74568786fbca6d5cf09
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556771"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="de93e-102">Postupy: Dešifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="de93e-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="de93e-103">Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k zašifrování a dešifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="de93e-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="de93e-104">Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="de93e-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="de93e-105">Další informace o standardu šifrování XML najdete v tématu [syntaxe a zpracování signatur XML](https://www.w3.org/TR/xmldsig-core/)doporučení pro konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="de93e-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  

> [!NOTE]
> <span data-ttu-id="de93e-106">Kód v tomto článku se vztahuje na systém Windows.</span><span class="sxs-lookup"><span data-stu-id="de93e-106">The code in this article applies to Windows.</span></span>

<span data-ttu-id="de93e-107">Příklad v tomto postupu dešifruje XML element, který byl zašifrován pomocí metod popsaných v tématu [Postupy: šifrování elementů XML pomocí asymetrických klíčů](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="de93e-107">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="de93e-108">Najde <`EncryptedData`> prvek, dešifruje prvek a poté nahradí element původním nešifrovaným elementem XML.</span><span class="sxs-lookup"><span data-stu-id="de93e-108">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="de93e-109">Tento příklad dešifruje XML element pomocí dvou klíčů.</span><span class="sxs-lookup"><span data-stu-id="de93e-109">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="de93e-110">Načte dříve vygenerovaný privátní klíč RSA z kontejneru klíčů a potom pomocí klíče RSA dešifruje klíč relace uložený v `EncryptedKey` prvku <> elementu <`EncryptedData`>.</span><span class="sxs-lookup"><span data-stu-id="de93e-110">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="de93e-111">Příklad poté používá klíč relace k dešifrování XML elementu.</span><span class="sxs-lookup"><span data-stu-id="de93e-111">The example then uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="de93e-112">Tento příklad je vhodný pro situace, kdy více aplikací musí sdílet šifrovaná data nebo kde aplikace musí ukládat šifrovaná data mezi časy, ve kterých je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="de93e-112">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="de93e-113">Dešifrování elementu XML pomocí asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="de93e-113">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="de93e-114">Vytvořte <xref:System.Security.Cryptography.CspParameters> objekt a zadejte název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="de93e-114">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="de93e-115">Načte dříve generovaný asymetrický klíč z kontejneru pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu.</span><span class="sxs-lookup"><span data-stu-id="de93e-115">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="de93e-116">Klíč je automaticky načten z kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="de93e-116">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="de93e-117">Vytvořte nový <xref:System.Security.Cryptography.Xml.EncryptedXml> objekt k dešifrování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="de93e-117">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="de93e-118">Přidejte mapování klíč/název pro přidružení klíče RSA k elementu v dokumentu, který má být dešifrován.</span><span class="sxs-lookup"><span data-stu-id="de93e-118">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="de93e-119">Pro klíč, který jste použili při šifrování dokumentu, je nutné použít stejný název.</span><span class="sxs-lookup"><span data-stu-id="de93e-119">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="de93e-120">Všimněte si, že tento název je oddělený od názvu používaného k identifikaci klíče v kontejneru klíčů zadaného v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="de93e-120">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="de93e-121">Zavolejte <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodu pro dešifrování <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="de93e-121">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="de93e-122">Tato metoda používá klíč RSA k dešifrování klíče relace a automaticky používá klíč relace k dešifrování XML elementu.</span><span class="sxs-lookup"><span data-stu-id="de93e-122">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="de93e-123">Také automaticky nahradí <`EncryptedData`> prvek původním prostým textem.</span><span class="sxs-lookup"><span data-stu-id="de93e-123">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="de93e-124">Uložte dokument XML.</span><span class="sxs-lookup"><span data-stu-id="de93e-124">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="de93e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="de93e-125">Example</span></span>

<span data-ttu-id="de93e-126">V tomto příkladu se předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="de93e-126">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="de93e-127">Předpokládá také, že `test.xml` obsahuje element XML, který byl zašifrován pomocí metod popsaných v tématu [How to: Encrypt XML Elements with asymetrické klíče](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="de93e-127">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de93e-128">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="de93e-128">Compiling the Code</span></span>  
  
- <span data-ttu-id="de93e-129">V projektu, který cílí na .NET Framework, zahrňte odkaz na `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="de93e-129">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="de93e-130">V projektu, který cílí na .NET Core nebo .NET 5, nainstalujte balíček NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="de93e-130">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="de93e-131">Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="de93e-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="de93e-132">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="de93e-132">.NET Security</span></span>  

<span data-ttu-id="de93e-133">Nikdy neukládejte symetrický kryptografický klíč ve formě prostého textu nebo přenášet symetrický klíč mezi počítači ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="de93e-133">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="de93e-134">Kromě toho nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="de93e-134">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="de93e-135">Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="de93e-135">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="de93e-136">Nikdy nevkládat klíč přímo do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="de93e-136">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="de93e-137">Vložené klíče lze snadno přečíst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="de93e-137">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="de93e-138">Až budete s použitím kryptografického klíče hotovi, vymažte ho z paměti nastavením každého bajtu na nulu nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="de93e-138">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="de93e-139">Kryptografické klíče je někdy možné z paměti načítat pomocí ladicího programu nebo je číst z pevného disku, pokud je umístění v paměti stránkované na disk.</span><span class="sxs-lookup"><span data-stu-id="de93e-139">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de93e-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="de93e-140">See also</span></span>

- [<span data-ttu-id="de93e-141">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="de93e-141">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="de93e-142">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="de93e-142">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="de93e-143">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="de93e-143">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="de93e-144">Postupy: Šifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="de93e-144">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="de93e-145">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="de93e-145">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
