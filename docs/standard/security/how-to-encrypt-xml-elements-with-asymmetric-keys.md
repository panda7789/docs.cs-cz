---
title: "Postupy: Šifrování elementů XML pomocí asymetrických klíčů"
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cadd6e5af8ed95da34091bc3a9f3ac8d5af4e9cb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="68b26-102">Postupy: Šifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="68b26-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="68b26-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro zašifrování element dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68b26-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="68b26-104">XML – šifrování je standardní způsob, jak exchange nebo uložit šifrovaná data XML, bez starostí o data snadno čitelná.</span><span class="sxs-lookup"><span data-stu-id="68b26-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="68b26-105">Další informace o standardu šifrování XML najdete v článku, že specifikace World Wide Web Consortium (W3C) pro šifrování XML nacházející se v http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="68b26-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="68b26-106">XML – šifrování vám pomůže nahradit libovolný element, XML nebo dokument <`EncryptedData`> elementu, který obsahuje šifrovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="68b26-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="68b26-107"><`EncryptedData`> Element může také obsahovat dílčí elementy, které obsahují informace o klíčích a postupech použitých při šifrování.</span><span class="sxs-lookup"><span data-stu-id="68b26-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="68b26-108">XML – šifrování umožňuje dokument obsahoval více šifrovaných elementů a umožňuje element k zašifrování vícekrát.</span><span class="sxs-lookup"><span data-stu-id="68b26-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="68b26-109">Příklad kódu v tomto postupu ukazuje postup vytvoření <`EncryptedData`> element společně s několika další dílčí prvky, které můžete použít později během dešifrování.</span><span class="sxs-lookup"><span data-stu-id="68b26-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="68b26-110">Tento příklad šifruje elementu XML s použitím dva klíče.</span><span class="sxs-lookup"><span data-stu-id="68b26-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="68b26-111">Generuje dvojici RSA veřejného a privátního klíče a uloží páru klíčů zabezpečeného kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="68b26-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="68b26-112">Tento příklad vytvoří oddělený klíč relace pomocí algoritmus Advanced Encryption (Standard AES), označované taky jako algoritmus Rijndael.</span><span class="sxs-lookup"><span data-stu-id="68b26-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm, also called the Rijndael algorithm.</span></span>  <span data-ttu-id="68b26-113">V příkladu používá klíč relace AES k šifrování dokumentu XML a pak používá k šifrování AES klíč relace veřejným klíčem RSA.</span><span class="sxs-lookup"><span data-stu-id="68b26-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="68b26-114">Nakonec příklad uloží zašifrovaný klíč relace a šifrovaná data XML v dokumentu XML v rámci nového <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="68b26-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="68b26-115">K dešifrování elementu XML, načtení privátního klíče RSA z kontejneru klíčů, použít ho k dešifrování klíče relace a pak použít klíč relace k dešifrování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="68b26-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="68b26-116">Další informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [postupy: dešifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="68b26-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="68b26-117">Tento příklad je vhodný pro situace, kdy je potřeba sdílet šifrovaná data více aplikací nebo pokud aplikace potřebuje k uložení šifrovaných dat v době mezi spuštěné.</span><span class="sxs-lookup"><span data-stu-id="68b26-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="68b26-118">K zašifrování elementu XML asymetrickým klíčem</span><span class="sxs-lookup"><span data-stu-id="68b26-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="68b26-119">Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="68b26-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="68b26-120">Generování symetrického klíče pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="68b26-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="68b26-121">Klíč je automaticky uloží do kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> objektu do konstruktoru objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="68b26-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="68b26-122">Tento klíč se použije k šifrování AES klíč relace a lze načíst později ho dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="68b26-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="68b26-123">Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="68b26-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="68b26-124"><xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.</span><span class="sxs-lookup"><span data-stu-id="68b26-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="68b26-125">Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte novou <xref:System.Xml.XmlElement> objekt představující element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="68b26-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="68b26-126">V tomto příkladu `"creditcard"` je zašifrován element.</span><span class="sxs-lookup"><span data-stu-id="68b26-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="68b26-127">Vytvoření nové relace klíče pomocí <xref:System.Security.Cryptography.RijndaelManaged> třídy.</span><span class="sxs-lookup"><span data-stu-id="68b26-127">Create a new session key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="68b26-128">Tento klíč bude šifrování elementu XML a pak se sám zašifrován a umístěny v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68b26-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="68b26-129">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použít ho k zašifrování daného elementu pomocí klíče relace.</span><span class="sxs-lookup"><span data-stu-id="68b26-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="68b26-130"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda vrací šifrovaný element jako pole bajtů šifrované.</span><span class="sxs-lookup"><span data-stu-id="68b26-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="68b26-131">Vytvořit <xref:System.Security.Cryptography.Xml.EncryptedData> objektu a jeho naplnění identifikátor URL šifrovaného elementu XML.</span><span class="sxs-lookup"><span data-stu-id="68b26-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="68b26-132">Tento identifikátor URL umožňuje dešifrování objektu strany vědět, že soubor XML obsahuje element šifrované.</span><span class="sxs-lookup"><span data-stu-id="68b26-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="68b26-133">Můžete použít <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pole k určení identifikátoru adresy URL.</span><span class="sxs-lookup"><span data-stu-id="68b26-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="68b26-134">Nahradí element XML ve formátu prostého textu <`EncryptedData`> element zapouzdřené to <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.</span><span class="sxs-lookup"><span data-stu-id="68b26-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="68b26-135">Vytvoření <xref:System.Security.Cryptography.Xml.EncryptionMethod> objekt, který je inicializován na identifikátor URL kryptografický algoritmus používaný k vygenerování klíče relace.</span><span class="sxs-lookup"><span data-stu-id="68b26-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="68b26-136">Předat <xref:System.Security.Cryptography.Xml.EncryptionMethod> do objektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="68b26-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="68b26-137">Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedKey> objektu obsahuje šifrovaný klíč relace.</span><span class="sxs-lookup"><span data-stu-id="68b26-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="68b26-138">Šifrování klíče relace, přidejte ho do <xref:System.Security.Cryptography.Xml.EncryptedKey> objektu a zadejte název klíče relace a klíče identifikátoru adresy URL.</span><span class="sxs-lookup"><span data-stu-id="68b26-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="68b26-139">Vytvořte novou <xref:System.Security.Cryptography.Xml.DataReference> objekt, který mapuje šifrovaná data na určitý klíč relace.</span><span class="sxs-lookup"><span data-stu-id="68b26-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="68b26-140">Tento volitelný krok vám umožní snadno určit více částí dokumentu XML byly zašifrovaly jeden klíč.</span><span class="sxs-lookup"><span data-stu-id="68b26-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="68b26-141">Přidat šifrovaný klíč do <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.</span><span class="sxs-lookup"><span data-stu-id="68b26-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="68b26-142">Vytvořte novou <xref:System.Security.Cryptography.Xml.KeyInfo> objektu k zadání názvu klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="68b26-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="68b26-143">Ho přidat do <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.</span><span class="sxs-lookup"><span data-stu-id="68b26-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="68b26-144">To pomáhá dešifrování objektu strany identifikovat správný asymetrický klíč používat k dešifrování klíče relace.</span><span class="sxs-lookup"><span data-stu-id="68b26-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="68b26-145">Přidat element šifrovaná data, která mají <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.</span><span class="sxs-lookup"><span data-stu-id="68b26-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="68b26-146">Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu s <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.</span><span class="sxs-lookup"><span data-stu-id="68b26-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="68b26-147">Uložit <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="68b26-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="68b26-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="68b26-148">Example</span></span>  
 <span data-ttu-id="68b26-149">Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="68b26-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="68b26-150">Dále předpokládá, že `"test.xml"` obsahuje `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="68b26-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="68b26-151">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít jej v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="68b26-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="68b26-152">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="68b26-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="68b26-153">Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="68b26-153">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="68b26-154">Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="68b26-154">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="68b26-155">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="68b26-155">.NET Framework Security</span></span>  
 <span data-ttu-id="68b26-156">Nikdy neukládají symetrický kryptografický klíč ve formátu prostého textu nebo přeneste symetrického klíče mezi počítači v podobě prostého textu.</span><span class="sxs-lookup"><span data-stu-id="68b26-156">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="68b26-157">Kromě toho nikdy uložení nebo přeneste privátní klíč pár asymetrických klíčů ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="68b26-157">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="68b26-158">Další informace o symetrické a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="68b26-158">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="68b26-159">Nikdy nevkládejte klíč přímo do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="68b26-159">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="68b26-160">Vložené klíče lze snadno přečíst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, například Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="68b26-160">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="68b26-161">Po dokončení pomocí kryptografického klíče, vymazat z paměti nastavením všech bajtů na nulu nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda spravované kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="68b26-161">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="68b26-162">Kryptografické klíče v některých případech můžete číst z paměti ladicí program nebo číst z pevného disku, pokud je stránkovaného umístění v paměti na disk.</span><span class="sxs-lookup"><span data-stu-id="68b26-162">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b26-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="68b26-163">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="68b26-164">Postupy: Dešifrování elementů XML pomocí asymetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="68b26-164">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
