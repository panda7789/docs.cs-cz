---
title: 'Postupy: Dešifrování elementů XML pomocí symetrických klíčů'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: 8c9f75442e04b76369b5b2c5c1b266ce2a511a63
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555744"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="49958-102">Postupy: Dešifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="49958-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="49958-103">Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k zašifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="49958-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="49958-104">Šifrování XML umožňuje ukládat nebo přenášet citlivé XML, aniž byste se museli starat o data, která se dají snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="49958-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="49958-105">Tento příklad kódu dešifruje XML element pomocí algoritmu standard AES (Advanced Encryption Standard) (AES).</span><span class="sxs-lookup"><span data-stu-id="49958-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>
  
 <span data-ttu-id="49958-106">Informace o tom, jak zašifrovat XML element pomocí tohoto postupu, naleznete v tématu [How to: ENCRYPT XML Elements with Symetrick Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="49958-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="49958-107">Pokud používáte symetrický algoritmus jako AES k šifrování dat XML, je nutné použít stejný klíč k šifrování a dešifrování dat XML.</span><span class="sxs-lookup"><span data-stu-id="49958-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="49958-108">V příkladu v tomto postupu se předpokládá, že zašifrovaný kód XML byl zašifrovaný pomocí stejného klíče a že zašifrované a dešifrovací strany souhlasí s algoritmem a klíčem, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="49958-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="49958-109">Tento příklad neukládá nebo šifruje klíč AES v rámci šifrovaného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="49958-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="49958-110">Tento příklad je vhodný pro situace, kdy jedna aplikace potřebuje šifrovat data na základě klíče relace uloženého v paměti nebo na základě kryptograficky silného klíče odvozeného od hesla.</span><span class="sxs-lookup"><span data-stu-id="49958-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="49958-111">V situacích, kdy je potřeba, aby dvě nebo více aplikací sdílely šifrovaná data XML, zvažte použití schématu šifrování založeného na asymetrickém algoritmu nebo certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="49958-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="49958-112">Dešifrování elementu XML symetrickým klíčem</span><span class="sxs-lookup"><span data-stu-id="49958-112">To decrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="49958-113">Šifrujte XML element pomocí dříve vygenerovaného klíče pomocí technik popsaných v tématu [Postupy: šifrování elementů XML pomocí symetrických klíčů](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="49958-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2. <span data-ttu-id="49958-114">Vyhledejte prvek <`EncryptedData`> (definovaný standardem šifrování XML) v <xref:System.Xml.XmlDocument> objektu, který obsahuje šifrovaný kód XML a vytvořte nový <xref:System.Xml.XmlElement> objekt pro reprezentaci tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="49958-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. <span data-ttu-id="49958-115">Vytvořte <xref:System.Security.Cryptography.Xml.EncryptedData> objekt načtením nezpracovaných dat XML z dříve vytvořeného <xref:System.Xml.XmlElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="49958-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <span data-ttu-id="49958-116">Vytvořte nový <xref:System.Security.Cryptography.Xml.EncryptedXml> objekt a použijte ho k dešifrování dat XML pomocí stejného klíče, který se použil pro šifrování.</span><span class="sxs-lookup"><span data-stu-id="49958-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. <span data-ttu-id="49958-117">Nahraďte zašifrovaný element nově dešifrovaným nešifrovaným elementem v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="49958-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="49958-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="49958-118">Example</span></span>  
 <span data-ttu-id="49958-119">V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="49958-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="49958-120">Také předpokládá, že `"test.xml"` obsahuje `"creditcard"` element.</span><span class="sxs-lookup"><span data-stu-id="49958-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="49958-121">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="49958-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49958-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="49958-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="49958-123">V projektu, který cílí na .NET Framework, zahrňte odkaz na `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="49958-123">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="49958-124">V projektu, který cílí na .NET Core nebo .NET 5, nainstalujte balíček NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="49958-124">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="49958-125">Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="49958-125">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="49958-126">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="49958-126">.NET Security</span></span>
  
<span data-ttu-id="49958-127">Nikdy neukládejte kryptografický klíč ve formátu prostého textu ani nepřenáší klíč mezi počítači ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="49958-127">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
<span data-ttu-id="49958-128">Po dokončení používání symetrického kryptografického klíče jej vymažte z paměti nastavením každého bajtu na hodnotu nula nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="49958-128">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49958-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="49958-129">See also</span></span>

- [<span data-ttu-id="49958-130">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="49958-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="49958-131">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="49958-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="49958-132">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="49958-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="49958-133">Postupy: Šifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="49958-133">How to: Encrypt XML Elements with Symmetric Keys</span></span>](how-to-encrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="49958-134">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49958-134">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
