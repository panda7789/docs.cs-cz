---
title: 'Postupy: Šifrování XML elementů pomocí certifikátů X.509'
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
ms.openlocfilehash: 9cdd8e52be11eeba86ec406510f40f1a08809ff8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277216"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="c7a94-102">Postupy: Šifrování XML elementů pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="c7a94-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="c7a94-103">Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k zašifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c7a94-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="c7a94-104">Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="c7a94-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="c7a94-105">Další informace o standardu šifrování XML naleznete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML v umístění <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="c7a94-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="c7a94-106">Můžete použít šifrování XML k nahrazení libovolného elementu XML nebo dokumentu `EncryptedData` elementem <>, který obsahuje šifrovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="c7a94-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="c7a94-107">Prvek <`EncryptedData`> může obsahovat dílčí prvky, které obsahují informace o klíčích a procesech použitých při šifrování.</span><span class="sxs-lookup"><span data-stu-id="c7a94-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="c7a94-108">Šifrování XML umožňuje dokumentu obsahovat více šifrovaných prvků a umožňuje vícenásobné šifrování elementu.</span><span class="sxs-lookup"><span data-stu-id="c7a94-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="c7a94-109">Příklad kódu v tomto postupu ukazuje, jak vytvořit `EncryptedData` prvek <> spolu s několika dalšími dílčími prvky, které můžete použít později během dešifrování.</span><span class="sxs-lookup"><span data-stu-id="c7a94-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="c7a94-110">Tento příklad šifruje XML element pomocí dvou klíčů.</span><span class="sxs-lookup"><span data-stu-id="c7a94-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="c7a94-111">Vygeneruje testovací certifikát X. 509 pomocí nástroje pro [Vytvoření certifikátu (Makecert. exe)](/windows/desktop/SecCrypto/makecert) a uloží certifikát do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="c7a94-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) and saves the certificate to a certificate store.</span></span> <span data-ttu-id="c7a94-112">Příklad následně programově načte certifikát a použije ho k zašifrování XML elementu pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7a94-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="c7a94-113">Interně <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda vytvoří samostatný klíč relace a použije ho k zašifrování dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c7a94-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="c7a94-114">Tato metoda šifruje klíč relace a uloží jej spolu s šifrovaným XML v rámci nového <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="c7a94-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="c7a94-115">Chcete-li dešifrovat XML element, jednoduše zavolejte <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodu, která automaticky načte certifikát X. 509 z úložiště a provede nezbytné dešifrování.</span><span class="sxs-lookup"><span data-stu-id="c7a94-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="c7a94-116">Další informace o tom, jak dešifrovat XML element, který byl zašifrován pomocí tohoto postupu, naleznete v tématu [How to: Dešifrujte XML Elements pomocí certifikátů X. 509](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="c7a94-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="c7a94-117">Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.</span><span class="sxs-lookup"><span data-stu-id="c7a94-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="c7a94-118">Šifrování elementu XML pomocí certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="c7a94-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="c7a94-119">Pomocí [Nástroje pro tvorbu certifikátů (Makecert. exe)](/windows/desktop/SecCrypto/makecert) vygenerujte testovací certifikát X. 509 a umístěte ho do úložiště místního uživatele.</span><span class="sxs-lookup"><span data-stu-id="c7a94-119">Use the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="c7a94-120">Musíte vygenerovat klíč pro výměnu a musíte si klíč exportovat.</span><span class="sxs-lookup"><span data-stu-id="c7a94-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="c7a94-121">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c7a94-121">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="c7a94-122">Vytvořte <xref:System.Security.Cryptography.X509Certificates.X509Store> objekt a inicializujte ho pro otevření aktuálního úložiště uživatele.</span><span class="sxs-lookup"><span data-stu-id="c7a94-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="c7a94-123">Otevřete Store v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c7a94-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="c7a94-124">Inicializujte <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> všechny certifikáty v úložišti.</span><span class="sxs-lookup"><span data-stu-id="c7a94-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="c7a94-125">Zobrazte výčet certifikátů ve Storu a vyhledejte certifikát s příslušným názvem.</span><span class="sxs-lookup"><span data-stu-id="c7a94-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="c7a94-126">V tomto příkladu se certifikát jmenuje `"CN=XML_ENC_TEST_CERT"` .</span><span class="sxs-lookup"><span data-stu-id="c7a94-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="c7a94-127">Po umístění certifikátu zavřete úložiště.</span><span class="sxs-lookup"><span data-stu-id="c7a94-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="c7a94-128">Vytvořte <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="c7a94-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="c7a94-129"><xref:System.Xml.XmlDocument>Objekt obsahuje element XML k zašifrování.</span><span class="sxs-lookup"><span data-stu-id="c7a94-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="c7a94-130">Vyhledá zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvoří nový <xref:System.Xml.XmlElement> objekt, který reprezentuje element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="c7a94-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="c7a94-131">V tomto příkladu `"creditcard"` je element zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="c7a94-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="c7a94-132">Vytvořte novou instanci <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použijte ji k zašifrování zadaného elementu pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="c7a94-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="c7a94-133"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>Metoda vrátí zašifrovaný prvek jako <xref:System.Security.Cryptography.Xml.EncryptedData> objekt.</span><span class="sxs-lookup"><span data-stu-id="c7a94-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="c7a94-134">Nahraďte element z původního <xref:System.Xml.XmlDocument> objektu <xref:System.Security.Cryptography.Xml.EncryptedData> elementem.</span><span class="sxs-lookup"><span data-stu-id="c7a94-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="c7a94-135">Uložte <xref:System.Xml.XmlDocument> objekt.</span><span class="sxs-lookup"><span data-stu-id="c7a94-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="c7a94-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7a94-136">Example</span></span>  
 <span data-ttu-id="c7a94-137">V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="c7a94-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="c7a94-138">Také předpokládá, že `"test.xml"` obsahuje `"creditcard"` element.</span><span class="sxs-lookup"><span data-stu-id="c7a94-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="c7a94-139">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7a94-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7a94-140">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c7a94-140">Compiling the Code</span></span>  
  
- <span data-ttu-id="c7a94-141">Chcete-li tento příklad zkompilovat, je nutné zahrnout odkaz na `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="c7a94-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="c7a94-142">Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="c7a94-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c7a94-143">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c7a94-143">.NET Framework Security</span></span>  
 <span data-ttu-id="c7a94-144">Certifikát X. 509 použitý v tomto příkladu je určen pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="c7a94-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="c7a94-145">Aplikace by měly používat certifikát X. 509 vygenerovaný důvěryhodnou certifikační autoritou nebo používat certifikát vygenerovaný serverem Microsoft Windows Certificate Server.</span><span class="sxs-lookup"><span data-stu-id="c7a94-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a94-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7a94-146">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="c7a94-147">Postupy: Dešifrování XML elementů pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="c7a94-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](how-to-decrypt-xml-elements-with-x-509-certificates.md)
