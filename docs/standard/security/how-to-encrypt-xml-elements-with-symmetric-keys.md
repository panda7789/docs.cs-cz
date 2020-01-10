---
title: 'Postupy: Šifrování elementů XML pomocí symetrických klíčů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: cda5a32e9a7421cd65b2046b403fde9e05230493
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706081"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="394cd-102">Postupy: Šifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="394cd-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="394cd-103">Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="394cd-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="394cd-104">Šifrování XML umožňuje ukládat nebo přenášet citlivé XML, aniž byste se museli starat o data, která se dají snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="394cd-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="394cd-105">Tento postup šifruje XML element pomocí algoritmu standard AES (Advanced Encryption Standard) (AES), označovaného také jako Rijndael.</span><span class="sxs-lookup"><span data-stu-id="394cd-105">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="394cd-106">Informace o tom, jak dešifrovat XML element, který byl zašifrován pomocí tohoto postupu, naleznete v tématu [How to: deencrypt XML Elements with Symetrick Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="394cd-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="394cd-107">Pokud používáte symetrický algoritmus jako AES k šifrování dat XML, je nutné použít stejný klíč k šifrování a dešifrování dat XML.</span><span class="sxs-lookup"><span data-stu-id="394cd-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="394cd-108">V příkladu v tomto postupu se předpokládá, že zašifrovaný kód XML bude dešifrován pomocí stejného klíče a že zašifrované a dešifrovací strany souhlasí s algoritmem a klíčem, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="394cd-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="394cd-109">Tento příklad neukládá nebo šifruje klíč AES v rámci šifrovaného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="394cd-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="394cd-110">Tento příklad je vhodný pro situace, kdy jedna aplikace potřebuje šifrovat data na základě klíče relace uloženého v paměti nebo na základě kryptograficky silného klíče odvozeného od hesla.</span><span class="sxs-lookup"><span data-stu-id="394cd-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="394cd-111">V situacích, kdy je potřeba, aby dvě nebo více aplikací sdílely šifrovaná data XML, zvažte použití schématu šifrování založeného na asymetrickém algoritmu nebo certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="394cd-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="394cd-112">Šifrování elementu XML pomocí symetrického klíče</span><span class="sxs-lookup"><span data-stu-id="394cd-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="394cd-113">Vygenerujte symetrický klíč pomocí třídy <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="394cd-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="394cd-114">Tento klíč se použije k zašifrování elementu XML.</span><span class="sxs-lookup"><span data-stu-id="394cd-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="394cd-115">Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="394cd-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="394cd-116">Objekt <xref:System.Xml.XmlDocument> obsahuje element XML k zašifrování.</span><span class="sxs-lookup"><span data-stu-id="394cd-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="394cd-117">Vyhledá zadaný element v objektu <xref:System.Xml.XmlDocument> a vytvoří nový objekt <xref:System.Xml.XmlElement>, který reprezentuje element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="394cd-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="394cd-118">V tomto příkladu je prvek `"creditcard"` zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="394cd-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="394cd-119">Vytvořte novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> a použijte ji k zašifrování <xref:System.Xml.XmlElement> symetrického klíče.</span><span class="sxs-lookup"><span data-stu-id="394cd-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="394cd-120">Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> vrátí zašifrovaný prvek jako pole šifrovaných bajtů.</span><span class="sxs-lookup"><span data-stu-id="394cd-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="394cd-121">Sestavte objekt <xref:System.Security.Cryptography.Xml.EncryptedData> a naplňte ho identifikátorem URL XML elementu šifrování.</span><span class="sxs-lookup"><span data-stu-id="394cd-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="394cd-122">Tento identifikátor adresy URL umožňuje dešifrovací straně upozornit, že kód XML obsahuje zašifrovaný element.</span><span class="sxs-lookup"><span data-stu-id="394cd-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="394cd-123">K určení identifikátoru adresy URL můžete použít pole <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>.</span><span class="sxs-lookup"><span data-stu-id="394cd-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="394cd-124">Vytvořte objekt <xref:System.Security.Cryptography.Xml.EncryptionMethod>, který je inicializován na identifikátor adresy URL kryptografického algoritmu použitého k vygenerování klíče.</span><span class="sxs-lookup"><span data-stu-id="394cd-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="394cd-125">Předejte objekt <xref:System.Security.Cryptography.Xml.EncryptionMethod> do vlastnosti <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.</span><span class="sxs-lookup"><span data-stu-id="394cd-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="394cd-126">Přidejte data šifrovaných prvků do objektu <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="394cd-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="394cd-127">Nahraďte prvek z původního objektu <xref:System.Xml.XmlDocument> prvkem <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="394cd-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="394cd-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="394cd-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="394cd-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="394cd-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="394cd-130">Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="394cd-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="394cd-131">Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="394cd-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="394cd-132">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="394cd-132">.NET Framework Security</span></span>  
 <span data-ttu-id="394cd-133">Nikdy neukládejte kryptografický klíč ve formátu prostého textu ani nepřenáší klíč mezi počítači ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="394cd-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="394cd-134">Místo toho použijte k ukládání kryptografických klíčů zabezpečený kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="394cd-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="394cd-135">Až budete s použitím kryptografického klíče hotovi, vymažte ho z paměti nastavením každého bajtu na nulu nebo voláním metody <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="394cd-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394cd-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="394cd-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="394cd-137">Postupy: Dešifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="394cd-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
