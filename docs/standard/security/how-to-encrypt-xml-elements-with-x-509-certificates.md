---
title: 'Postupy: Šifrování elementů XML pomocí certifikátů X.509'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], X.509 certificates
- cryptography [.NET], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: c978bea7336e64d6622aca4d21c7ef3317d73957
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555718"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="08ba0-102">Postupy: Šifrování elementů XML pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="08ba0-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="08ba0-103">Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k zašifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="08ba0-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="08ba0-104">Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="08ba0-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="08ba0-105">Další informace o standardu šifrování XML naleznete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML v umístění <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="08ba0-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="08ba0-106">Můžete použít šifrování XML k nahrazení libovolného elementu XML nebo dokumentu `EncryptedData` elementem <>, který obsahuje šifrovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="08ba0-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="08ba0-107">Prvek <`EncryptedData`> může obsahovat dílčí prvky, které obsahují informace o klíčích a procesech použitých při šifrování.</span><span class="sxs-lookup"><span data-stu-id="08ba0-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="08ba0-108">Šifrování XML umožňuje dokumentu obsahovat více šifrovaných prvků a umožňuje vícenásobné šifrování elementu.</span><span class="sxs-lookup"><span data-stu-id="08ba0-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="08ba0-109">Příklad kódu v tomto postupu ukazuje, jak vytvořit `EncryptedData` prvek <> spolu s několika dalšími dílčími prvky, které můžete použít později během dešifrování.</span><span class="sxs-lookup"><span data-stu-id="08ba0-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
<span data-ttu-id="08ba0-110">Tento příklad šifruje XML element pomocí dvou klíčů.</span><span class="sxs-lookup"><span data-stu-id="08ba0-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="08ba0-111">Příklad programově načte certifikát a použije ho k zašifrování XML elementu pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="08ba0-111">The example programmatically retrieves a certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="08ba0-112">Interně <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda vytvoří samostatný klíč relace a použije ho k zašifrování dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="08ba0-112">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="08ba0-113">Tato metoda šifruje klíč relace a uloží jej spolu s šifrovaným XML v rámci nového <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="08ba0-113">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  

<span data-ttu-id="08ba0-114">Chcete-li dešifrovat XML element, zavolejte <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodu, která automaticky načte certifikát X. 509 z úložiště a provede nezbytné dešifrování.</span><span class="sxs-lookup"><span data-stu-id="08ba0-114">To decrypt the XML element, call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="08ba0-115">Další informace o tom, jak dešifrovat XML element, který byl zašifrován pomocí tohoto postupu, naleznete v tématu [How to: Dešifrujte XML Elements pomocí certifikátů X. 509](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="08ba0-115">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
<span data-ttu-id="08ba0-116">Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.</span><span class="sxs-lookup"><span data-stu-id="08ba0-116">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="08ba0-117">Šifrování elementu XML pomocí certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="08ba0-117">To encrypt an XML element with an X.509 certificate</span></span>  

<span data-ttu-id="08ba0-118">Chcete-li spustit tento příklad, musíte vytvořit testovací certifikát a uložit ho do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="08ba0-118">To run this example, you need to create a test certificate and save it in a certificate store.</span></span> <span data-ttu-id="08ba0-119">Pokyny k této úloze jsou k dispozici pouze pro [Nástroj pro vytváření certifikátů systému Windows (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="08ba0-119">Instructions for that task are provided only for the Windows [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span></span>

1. <span data-ttu-id="08ba0-120">Pomocí [Makecert.exe](/windows/desktop/SecCrypto/makecert) vygenerujte testovací certifikát X. 509 a umístěte ho do úložiště místního uživatele.</span><span class="sxs-lookup"><span data-stu-id="08ba0-120">Use [Makecert.exe](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="08ba0-121">Musíte vygenerovat klíč pro výměnu a musíte si klíč exportovat.</span><span class="sxs-lookup"><span data-stu-id="08ba0-121">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="08ba0-122">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="08ba0-122">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="08ba0-123">Vytvořte <xref:System.Security.Cryptography.X509Certificates.X509Store> objekt a inicializujte ho pro otevření aktuálního úložiště uživatele.</span><span class="sxs-lookup"><span data-stu-id="08ba0-123">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="08ba0-124">Otevřete Store v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="08ba0-124">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="08ba0-125">Inicializujte <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> všechny certifikáty v úložišti.</span><span class="sxs-lookup"><span data-stu-id="08ba0-125">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="08ba0-126">Zobrazte výčet certifikátů ve Storu a vyhledejte certifikát s příslušným názvem.</span><span class="sxs-lookup"><span data-stu-id="08ba0-126">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="08ba0-127">V tomto příkladu se certifikát jmenuje `"CN=XML_ENC_TEST_CERT"` .</span><span class="sxs-lookup"><span data-stu-id="08ba0-127">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="08ba0-128">Po umístění certifikátu zavřete úložiště.</span><span class="sxs-lookup"><span data-stu-id="08ba0-128">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="08ba0-129">Vytvořte <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="08ba0-129">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="08ba0-130"><xref:System.Xml.XmlDocument>Objekt obsahuje element XML k zašifrování.</span><span class="sxs-lookup"><span data-stu-id="08ba0-130">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="08ba0-131">Vyhledá zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvoří nový <xref:System.Xml.XmlElement> objekt, který reprezentuje element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="08ba0-131">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="08ba0-132">V tomto příkladu `"creditcard"` je element zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="08ba0-132">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="08ba0-133">Vytvořte novou instanci <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použijte ji k zašifrování zadaného elementu pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="08ba0-133">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="08ba0-134"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>Metoda vrátí zašifrovaný prvek jako <xref:System.Security.Cryptography.Xml.EncryptedData> objekt.</span><span class="sxs-lookup"><span data-stu-id="08ba0-134">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="08ba0-135">Nahraďte element z původního <xref:System.Xml.XmlDocument> objektu <xref:System.Security.Cryptography.Xml.EncryptedData> elementem.</span><span class="sxs-lookup"><span data-stu-id="08ba0-135">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="08ba0-136">Uložte <xref:System.Xml.XmlDocument> objekt.</span><span class="sxs-lookup"><span data-stu-id="08ba0-136">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="08ba0-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="08ba0-137">Example</span></span>  
 <span data-ttu-id="08ba0-138">V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="08ba0-138">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="08ba0-139">Také předpokládá, že `"test.xml"` obsahuje `"creditcard"` element.</span><span class="sxs-lookup"><span data-stu-id="08ba0-139">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="08ba0-140">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="08ba0-140">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="08ba0-141">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="08ba0-141">Compiling the Code</span></span>  
  
- <span data-ttu-id="08ba0-142">V projektu, který cílí na .NET Framework, zahrňte odkaz na `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="08ba0-142">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="08ba0-143">V projektu, který cílí na .NET Core nebo .NET 5, nainstalujte balíček NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="08ba0-143">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="08ba0-144">Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="08ba0-144">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="08ba0-145">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="08ba0-145">.NET Security</span></span>
  
<span data-ttu-id="08ba0-146">Certifikát X. 509 použitý v tomto příkladu je určen pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="08ba0-146">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="08ba0-147">Aplikace by měly používat certifikát X. 509 generovaný důvěryhodnou certifikační autoritou.</span><span class="sxs-lookup"><span data-stu-id="08ba0-147">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ba0-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="08ba0-148">See also</span></span>

- [<span data-ttu-id="08ba0-149">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="08ba0-149">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="08ba0-150">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="08ba0-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="08ba0-151">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="08ba0-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="08ba0-152">Postupy: Dešifrování elementů XML pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="08ba0-152">How to: Decrypt XML Elements with X.509 Certificates</span></span>](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="08ba0-153">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="08ba0-153">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
