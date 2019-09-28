---
title: 'Postupy: Šifrování elementů XML pomocí certifikátů X.509'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], X.509 certificates
- cryptography [.NET Framework], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d569d3c020e7329d987e957f181b34c8cfbf941a
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353858"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="4794b-102">Postupy: Šifrování elementů XML pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="4794b-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="4794b-103">Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4794b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="4794b-104">Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="4794b-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="4794b-105">Další informace o standardu šifrování XML najdete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML umístěné na <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="4794b-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="4794b-106">Můžete použít šifrování XML k nahrazení libovolného elementu XML nebo dokumentu pomocí < elementu `EncryptedData` >, který obsahuje šifrovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="4794b-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="4794b-107">< Element `EncryptedData` > může obsahovat dílčí prvky, které obsahují informace o klíčích a procesech použitých při šifrování.</span><span class="sxs-lookup"><span data-stu-id="4794b-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="4794b-108">Šifrování XML umožňuje dokumentu obsahovat více šifrovaných prvků a umožňuje vícenásobné šifrování elementu.</span><span class="sxs-lookup"><span data-stu-id="4794b-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="4794b-109">Příklad kódu v tomto postupu ukazuje, jak vytvořit < prvek `EncryptedData` > spolu s několika dalšími dílčími prvky, které můžete použít později během dešifrování.</span><span class="sxs-lookup"><span data-stu-id="4794b-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="4794b-110">Tento příklad šifruje XML element pomocí dvou klíčů.</span><span class="sxs-lookup"><span data-stu-id="4794b-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="4794b-111">Vygeneruje testovací certifikát X. 509 pomocí nástroje pro [Vytvoření certifikátu (Makecert. exe)](/windows/desktop/SecCrypto/makecert) a uloží certifikát do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4794b-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) and saves the certificate to a certificate store.</span></span> <span data-ttu-id="4794b-112">Příklad následně programově načte certifikát a použije ho k zašifrování XML elementu pomocí metody <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>.</span><span class="sxs-lookup"><span data-stu-id="4794b-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="4794b-113">Interně metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> vytvoří samostatný klíč relace a použije ho k zašifrování dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4794b-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="4794b-114">Tato metoda šifruje klíč relace a uloží jej spolu s šifrovaným XML v rámci nového < elementu `EncryptedData` >.</span><span class="sxs-lookup"><span data-stu-id="4794b-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="4794b-115">Chcete-li dešifrovat XML element, jednoduše zavolejte metodu <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>, která automaticky načte certifikát X. 509 z úložiště a provede nezbytné dešifrování.</span><span class="sxs-lookup"><span data-stu-id="4794b-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="4794b-116">Další informace o tom, jak dešifrovat XML element, který byl zašifrovaný pomocí tohoto postupu, naleznete v tématu [How na: Dešifrování elementů XML pomocí certifikátů X. 509 @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="4794b-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="4794b-117">Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.</span><span class="sxs-lookup"><span data-stu-id="4794b-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="4794b-118">Šifrování elementu XML pomocí certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="4794b-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="4794b-119">Pomocí [Nástroje pro tvorbu certifikátů (Makecert. exe)](/windows/desktop/SecCrypto/makecert) vygenerujte testovací certifikát X. 509 a umístěte ho do úložiště místního uživatele.</span><span class="sxs-lookup"><span data-stu-id="4794b-119">Use the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="4794b-120">Musíte vygenerovat klíč pro výměnu a musíte si klíč exportovat.</span><span class="sxs-lookup"><span data-stu-id="4794b-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="4794b-121">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4794b-121">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="4794b-122">Vytvořit objekt <xref:System.Security.Cryptography.X509Certificates.X509Store> a inicializovat ho pro otevření aktuálního úložiště uživatele.</span><span class="sxs-lookup"><span data-stu-id="4794b-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="4794b-123">Otevřete Store v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4794b-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="4794b-124">Inicializujte <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> se všemi certifikáty v úložišti.</span><span class="sxs-lookup"><span data-stu-id="4794b-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="4794b-125">Zobrazte výčet certifikátů ve Storu a vyhledejte certifikát s příslušným názvem.</span><span class="sxs-lookup"><span data-stu-id="4794b-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="4794b-126">V tomto příkladu je certifikát nazvaný `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="4794b-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="4794b-127">Po umístění certifikátu zavřete úložiště.</span><span class="sxs-lookup"><span data-stu-id="4794b-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="4794b-128">Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="4794b-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="4794b-129">Objekt <xref:System.Xml.XmlDocument> obsahuje element XML, který se má zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="4794b-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="4794b-130">Vyhledá zadaný element v objektu @no__t 0 a vytvoří nový objekt <xref:System.Xml.XmlElement>, který reprezentuje element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="4794b-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="4794b-131">V tomto příkladu je prvek `"creditcard"` zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="4794b-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="4794b-132">Vytvořte novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> a použijte ji k zašifrování zadaného elementu pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="4794b-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="4794b-133">Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> vrátí šifrovaný element jako objekt <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="4794b-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="4794b-134">Nahraďte prvek z původního objektu <xref:System.Xml.XmlDocument> pomocí elementu <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="4794b-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="4794b-135">Uložte objekt <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="4794b-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="4794b-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="4794b-136">Example</span></span>  
 <span data-ttu-id="4794b-137">V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="4794b-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="4794b-138">Také předpokládá, že `"test.xml"` obsahuje prvek `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="4794b-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="4794b-139">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4794b-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4794b-140">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4794b-140">Compiling the Code</span></span>  
  
- <span data-ttu-id="4794b-141">Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="4794b-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="4794b-142">Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="4794b-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4794b-143">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4794b-143">.NET Framework Security</span></span>  
 <span data-ttu-id="4794b-144">Certifikát X. 509 použitý v tomto příkladu je určen pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="4794b-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="4794b-145">Aplikace by měly používat certifikát X. 509 vygenerovaný důvěryhodnou certifikační autoritou nebo používat certifikát vygenerovaný serverem Microsoft Windows Certificate Server.</span><span class="sxs-lookup"><span data-stu-id="4794b-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4794b-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4794b-146">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- <span data-ttu-id="4794b-147">[Postupy: Dešifrování elementů XML pomocí certifikátů X. 509 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="4794b-147">[How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)</span></span>
