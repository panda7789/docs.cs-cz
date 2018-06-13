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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 329569ea148542ff596057d9eb9efe2e95768341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589068"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="dae8b-102">Postupy: Dešifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="dae8b-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="dae8b-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování a dešifrování element dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="dae8b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="dae8b-104">XML – šifrování je standardní způsob, jak exchange nebo uložit šifrovaná data XML, bez starostí o data snadno čitelná.</span><span class="sxs-lookup"><span data-stu-id="dae8b-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="dae8b-105">Další informace o standardu XML – šifrování najdete v tématu doporučení World Wide Web Consortium (W3C) [syntaxe podpis XML a zpracování](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="dae8b-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="dae8b-106">V příkladu v tomto postupu dešifruje element XML, který byl zašifrován pomocí metody popsané v [postupy: šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="dae8b-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="dae8b-107">Najde <`EncryptedData`> elementu, element dešifruje a element nahradí původní element XML ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="dae8b-108">Tento příklad dešifruje element XML pomocí dva klíče.</span><span class="sxs-lookup"><span data-stu-id="dae8b-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="dae8b-109">Načte dříve vytvořený privátní klíč RSA z kontejneru klíčů, a pak používá klíč RSA k dešifrování klíče relace uloženy v <`EncryptedKey`> elementu <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="dae8b-110">V příkladu pak používá klíč relace k dešifrování elementu XML.</span><span class="sxs-lookup"><span data-stu-id="dae8b-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="dae8b-111">Tento příklad je vhodný pro situace, kdy se více aplikací mít sdílet šifrovaná data nebo které má aplikace uložit šifrovaná data v době mezi spuštěné.</span><span class="sxs-lookup"><span data-stu-id="dae8b-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="dae8b-112">Dešifrování elementu XML asymetrickým klíčem</span><span class="sxs-lookup"><span data-stu-id="dae8b-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="dae8b-113">Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="dae8b-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="dae8b-114">Načíst dříve vygenerovaný asymetrický klíč z kontejneru pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="dae8b-115">Klíč je automaticky načte z kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> do objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="dae8b-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="dae8b-116">Vytvořte novou <xref:System.Security.Cryptography.Xml.EncryptedXml> objektu k dešifrování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  <span data-ttu-id="dae8b-117">Přidáte mapování název klíče nebo klíče RSA přidružit elementu v dokumentu, který by měl být dešifrován.</span><span class="sxs-lookup"><span data-stu-id="dae8b-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="dae8b-118">Musíte použít stejný název pro klíč, který jste použili při šifrování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="dae8b-119">Všimněte si, že tento název je oddělený od název sloužící k identifikaci klíče v kontejneru klíčů v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="dae8b-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  <span data-ttu-id="dae8b-120">Volání <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda dešifrovat <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="dae8b-121">Tato metoda používá klíč RSA k dešifrování klíče relace a automaticky používá klíč relace k dešifrování elementu XML.</span><span class="sxs-lookup"><span data-stu-id="dae8b-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="dae8b-122">Také automaticky nahradí <`EncryptedData`> element s původní ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  <span data-ttu-id="dae8b-123">Uložte dokument XML.</span><span class="sxs-lookup"><span data-stu-id="dae8b-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="dae8b-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="dae8b-124">Example</span></span>  
 <span data-ttu-id="dae8b-125">Tento příklad předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="dae8b-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="dae8b-126">Dále předpokládá, že `test.xml` obsahuje element XML, který byl zašifrován pomocí technik popsaných v [postupy: šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="dae8b-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dae8b-127">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dae8b-127">Compiling the Code</span></span>  
  
-   <span data-ttu-id="dae8b-128">Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="dae8b-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="dae8b-129">Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="dae8b-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="dae8b-130">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dae8b-130">.NET Framework Security</span></span>  
 <span data-ttu-id="dae8b-131">Nikdy neukládají symetrický kryptografický klíč ve formátu prostého textu nebo přeneste symetrického klíče mezi počítači v podobě prostého textu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="dae8b-132">Kromě toho nikdy uložení nebo přeneste privátní klíč pár asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="dae8b-133">Další informace o symetrické a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="dae8b-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="dae8b-134">Nikdy nevkládejte klíč přímo do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="dae8b-135">Vložené klíče můžete snadno přečíst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, například Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="dae8b-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="dae8b-136">Po dokončení pomocí kryptografického klíče, vymazat z paměti nastavením všech bajtů na nulu nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="dae8b-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="dae8b-137">Kryptografické klíče v některých případech můžete číst z paměti ladicí program nebo číst z pevného disku, pokud je stránkovaného umístění v paměti na disk.</span><span class="sxs-lookup"><span data-stu-id="dae8b-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae8b-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="dae8b-138">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="dae8b-139">Postupy: Šifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="dae8b-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
