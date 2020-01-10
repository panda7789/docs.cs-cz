---
title: 'Postupy: Šifrování elementů XML pomocí asymetrických klíčů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
ms.openlocfilehash: 2ebf3f86ac550c0179b2e26879a7df128fd529e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706094"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="4e780-102">Postupy: Šifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="4e780-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="4e780-103">Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4e780-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="4e780-104">Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="4e780-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="4e780-105">Další informace o standardu šifrování XML najdete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML umístěné v <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="4e780-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="4e780-106">Můžete použít šifrování XML k nahrazení libovolného elementu XML nebo dokumentu pomocí <`EncryptedData`> elementu, který obsahuje šifrovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="4e780-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="4e780-107">Prvek <`EncryptedData`> může také obsahovat dílčí prvky, které obsahují informace o klíčích a procesech použitých při šifrování.</span><span class="sxs-lookup"><span data-stu-id="4e780-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="4e780-108">Šifrování XML umožňuje dokumentu obsahovat více šifrovaných prvků a umožňuje vícenásobné šifrování elementu.</span><span class="sxs-lookup"><span data-stu-id="4e780-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="4e780-109">Příklad kódu v tomto postupu ukazuje, jak vytvořit <`EncryptedData`> prvek spolu s několika dalšími dílčími prvky, které můžete použít později během dešifrování.</span><span class="sxs-lookup"><span data-stu-id="4e780-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="4e780-110">Tento příklad šifruje XML element pomocí dvou klíčů.</span><span class="sxs-lookup"><span data-stu-id="4e780-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="4e780-111">Vygeneruje pár veřejného a privátního klíče RSA a uloží dvojici klíčů do zabezpečeného kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="4e780-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="4e780-112">Příklad následně vytvoří samostatný klíč relace pomocí algoritmu standard AES (Advanced Encryption Standard) (AES), který se označuje také jako algoritmus Rijndael.</span><span class="sxs-lookup"><span data-stu-id="4e780-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm, also called the Rijndael algorithm.</span></span>  <span data-ttu-id="4e780-113">V příkladu je použit klíč relace AES k šifrování dokumentu XML a poté používá veřejný klíč RSA k šifrování klíče relace AES.</span><span class="sxs-lookup"><span data-stu-id="4e780-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="4e780-114">Nakonec příklad uloží šifrovaný klíč relace AES a zašifrovaná data XML do dokumentu XML v rámci nového <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="4e780-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="4e780-115">Chcete-li dešifrovat XML element, načtěte privátní klíč RSA z kontejneru klíčů, použijte ho k dešifrování klíče relace a pak použijte klíč relace k dešifrování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4e780-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="4e780-116">Další informace o tom, jak dešifrovat XML element, který byl zašifrovaný pomocí tohoto postupu, naleznete v tématu [How to: deencrypt XML Elements with asymetrické klíče](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="4e780-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="4e780-117">Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.</span><span class="sxs-lookup"><span data-stu-id="4e780-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="4e780-118">Šifrování elementu XML pomocí asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="4e780-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="4e780-119">Vytvořte objekt <xref:System.Security.Cryptography.CspParameters> a zadejte název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="4e780-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="4e780-120">Vygenerujte symetrický klíč pomocí třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="4e780-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="4e780-121">Klíč se automaticky uloží do kontejneru klíčů při předání objektu <xref:System.Security.Cryptography.CspParameters> do konstruktoru třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="4e780-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="4e780-122">Tento klíč se použije k zašifrování klíče relace AES a bude možné ho později načíst k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="4e780-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="4e780-123">Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="4e780-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="4e780-124">Objekt <xref:System.Xml.XmlDocument> obsahuje element XML k zašifrování.</span><span class="sxs-lookup"><span data-stu-id="4e780-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="4e780-125">Vyhledá zadaný element v objektu <xref:System.Xml.XmlDocument> a vytvoří nový objekt <xref:System.Xml.XmlElement>, který reprezentuje element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="4e780-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="4e780-126">V tomto příkladu je prvek `"creditcard"` zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="4e780-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="4e780-127">Vytvořte nový klíč relace pomocí třídy <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="4e780-127">Create a new session key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="4e780-128">Tento klíč zašifruje XML element a pak bude zašifrovaný a umístěný v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4e780-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="4e780-129">Vytvořte novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> a použijte ji k zašifrování zadaného elementu pomocí klíče relace.</span><span class="sxs-lookup"><span data-stu-id="4e780-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="4e780-130">Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> vrátí zašifrovaný prvek jako pole šifrovaných bajtů.</span><span class="sxs-lookup"><span data-stu-id="4e780-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="4e780-131">Sestavte objekt <xref:System.Security.Cryptography.Xml.EncryptedData> a naplňte ho identifikátorem URL šifrovaného elementu XML.</span><span class="sxs-lookup"><span data-stu-id="4e780-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="4e780-132">Tento identifikátor adresy URL umožňuje dešifrovací straně upozornit, že kód XML obsahuje zašifrovaný element.</span><span class="sxs-lookup"><span data-stu-id="4e780-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="4e780-133">K určení identifikátoru adresy URL můžete použít pole <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>.</span><span class="sxs-lookup"><span data-stu-id="4e780-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="4e780-134">Nešifrovaný element XML bude nahrazen <`EncryptedData`> element zapouzdřený tímto <xref:System.Security.Cryptography.Xml.EncryptedData>m objektem.</span><span class="sxs-lookup"><span data-stu-id="4e780-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="4e780-135">Vytvořte objekt <xref:System.Security.Cryptography.Xml.EncryptionMethod>, který je inicializován na identifikátor adresy URL kryptografického algoritmu používaného k vygenerování klíče relace.</span><span class="sxs-lookup"><span data-stu-id="4e780-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="4e780-136">Předejte objekt <xref:System.Security.Cryptography.Xml.EncryptionMethod> do vlastnosti <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e780-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="4e780-137">Vytvořte objekt <xref:System.Security.Cryptography.Xml.EncryptedKey>, který bude obsahovat zašifrovaný klíč relace.</span><span class="sxs-lookup"><span data-stu-id="4e780-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="4e780-138">Zašifrujte klíč relace, přidejte ho do objektu <xref:System.Security.Cryptography.Xml.EncryptedKey> a zadejte název klíče relace a adresu URL identifikátoru klíče.</span><span class="sxs-lookup"><span data-stu-id="4e780-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="4e780-139">Vytvoří nový objekt <xref:System.Security.Cryptography.Xml.DataReference>, který mapuje šifrovaná data na konkrétní klíč relace.</span><span class="sxs-lookup"><span data-stu-id="4e780-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="4e780-140">Tento volitelný krok umožňuje snadno určit, že více částí dokumentu XML bylo zašifrováno jedním klíčem.</span><span class="sxs-lookup"><span data-stu-id="4e780-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="4e780-141">Přidejte šifrovaný klíč do objektu <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="4e780-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="4e780-142">Vytvořte nový objekt <xref:System.Security.Cryptography.Xml.KeyInfo> pro zadání názvu klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="4e780-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="4e780-143">Přidejte jej do objektu <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="4e780-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="4e780-144">To pomáhá dešifrovací straně identifikovat správný asymetrický klíč, který se má použít při dešifrování klíče relace.</span><span class="sxs-lookup"><span data-stu-id="4e780-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="4e780-145">Přidejte data šifrovaných prvků do objektu <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="4e780-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="4e780-146">Nahraďte prvek z původního objektu <xref:System.Xml.XmlDocument> prvkem <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="4e780-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="4e780-147">Uložte objekt <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="4e780-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="4e780-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e780-148">Example</span></span>  
 <span data-ttu-id="4e780-149">V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="4e780-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="4e780-150">Předpokládá také, že `"test.xml"` obsahuje `"creditcard"` prvek.</span><span class="sxs-lookup"><span data-stu-id="4e780-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="4e780-151">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4e780-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e780-152">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4e780-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="4e780-153">Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="4e780-153">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="4e780-154">Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="4e780-154">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4e780-155">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e780-155">.NET Framework Security</span></span>  
 <span data-ttu-id="4e780-156">Nikdy neukládejte symetrický kryptografický klíč ve formě prostého textu nebo přenášet symetrický klíč mezi počítači ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="4e780-156">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="4e780-157">Kromě toho nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="4e780-157">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="4e780-158">Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="4e780-158">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="4e780-159">Nikdy nevkládat klíč přímo do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4e780-159">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="4e780-160">Vložené klíče lze snadno přečíst ze sestavení pomocí nástroje [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="4e780-160">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="4e780-161">Až budete s použitím kryptografického klíče hotovi, vymažte ho z paměti nastavením každého bajtu na nulu nebo voláním metody <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="4e780-161">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="4e780-162">Kryptografické klíče je někdy možné z paměti načítat pomocí ladicího programu nebo je číst z pevného disku, pokud je umístění v paměti stránkované na disk.</span><span class="sxs-lookup"><span data-stu-id="4e780-162">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e780-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e780-163">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="4e780-164">Postupy: Dešifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="4e780-164">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
