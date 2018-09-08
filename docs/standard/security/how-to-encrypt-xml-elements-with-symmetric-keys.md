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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5c221dc05787c6d76d998977069ad327a3dfa83
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177198"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="4d616-102">Postupy: Šifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="4d616-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="4d616-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování element v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4d616-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="4d616-104">Šifrování XML můžete uložit nebo přenosu citlivých XML, nemusíme mít starosti se snadno číst data.</span><span class="sxs-lookup"><span data-stu-id="4d616-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="4d616-105">Tento postup dešifruje elementu XML použitím algoritmus Advanced Encryption (Standard AES), také označován jako Rijndael.</span><span class="sxs-lookup"><span data-stu-id="4d616-105">This procedure decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="4d616-106">Informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [postupy: dešifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="4d616-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="4d616-107">Při použití symetrický algoritmus, jako je AES pro šifrování dat XML, musí používat stejný klíč k šifrování a dešifrování dat XML.</span><span class="sxs-lookup"><span data-stu-id="4d616-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="4d616-108">V příkladu v tomto postupu předpokládá, že budou šifrované XML dešifrována pomocí stejného klíče a, že šifrování a dešifrování strany shodnout na algoritmus a klíč.</span><span class="sxs-lookup"><span data-stu-id="4d616-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="4d616-109">V tomto příkladu se neukládají ani šifrování AES klíč v souboru XML zašifrované.</span><span class="sxs-lookup"><span data-stu-id="4d616-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="4d616-110">Tento příklad je vhodný pro situace, kdy jedné aplikace potřebuje k šifrování dat na základě relace klíče uložené v paměti, nebo podle přidělení kryptograficky silného klíče odvozeného z hesla.</span><span class="sxs-lookup"><span data-stu-id="4d616-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="4d616-111">V situacích, kdy je potřeba sdílet šifrovaná data XML dva nebo více aplikací zvažte použití schématu šifrování na základě asymetrického algoritmu nebo certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="4d616-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="4d616-112">K šifrování se symetrickým klíčem XML element</span><span class="sxs-lookup"><span data-stu-id="4d616-112">To encrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="4d616-113">Vygenerovat symetrický klíč pomocí <xref:System.Security.Cryptography.RijndaelManaged> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d616-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="4d616-114">Tento klíč se použije k zašifrování XML element.</span><span class="sxs-lookup"><span data-stu-id="4d616-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="4d616-115">Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="4d616-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="4d616-116"><xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.</span><span class="sxs-lookup"><span data-stu-id="4d616-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="4d616-117">Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte nový <xref:System.Xml.XmlElement> objekt reprezentující element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="4d616-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="4d616-118">V tomto příkladu `"creditcard"` šifrovaná prvku.</span><span class="sxs-lookup"><span data-stu-id="4d616-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="4d616-119">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a jeho pomocí šifrovat <xref:System.Xml.XmlElement> pomocí symetrického klíče.</span><span class="sxs-lookup"><span data-stu-id="4d616-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="4d616-120"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda vrátí šifrovaný element jako pole šifrovaných bajtů.</span><span class="sxs-lookup"><span data-stu-id="4d616-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="4d616-121">Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedData> objektu a jeho naplnění identifikátor URL elementu šifrování XML.</span><span class="sxs-lookup"><span data-stu-id="4d616-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="4d616-122">Tento identifikátor URL umožňuje dešifrování strana vědět, že kód XML obsahuje šifrovaný element.</span><span class="sxs-lookup"><span data-stu-id="4d616-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="4d616-123">Můžete použít <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pole k určení identifikátoru adresy URL.</span><span class="sxs-lookup"><span data-stu-id="4d616-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="4d616-124">Vytvoření <xref:System.Security.Cryptography.Xml.EncryptionMethod> , který je inicializován na identifikátor URL kryptografický algoritmus používaný k vygenerování klíče.</span><span class="sxs-lookup"><span data-stu-id="4d616-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="4d616-125">Předání <xref:System.Security.Cryptography.Xml.EncryptionMethod> objektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4d616-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="4d616-126">Přidat data šifrovaný element <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d616-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="4d616-127">Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.</span><span class="sxs-lookup"><span data-stu-id="4d616-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="4d616-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d616-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d616-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4d616-129">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4d616-130">Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="4d616-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="4d616-131">Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="4d616-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4d616-132">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d616-132">.NET Framework Security</span></span>  
 <span data-ttu-id="4d616-133">Nikdy uložení kryptografického klíče ve formátu prostého textu nebo přenosu klíče mezi počítači ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="4d616-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="4d616-134">Místo toho použijte zabezpečené kontejneru klíčů pro ukládání kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="4d616-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="4d616-135">Po dokončení pomocí kryptografického klíče, vymažte ho z paměti nastavením všech bajtů na hodnotu nula nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda třídy spravované kryptografie.</span><span class="sxs-lookup"><span data-stu-id="4d616-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d616-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d616-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="4d616-137">Postupy: Dešifrování elementů XML pomocí symetrických klíčů</span><span class="sxs-lookup"><span data-stu-id="4d616-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
