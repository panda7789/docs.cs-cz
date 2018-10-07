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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3d61fcbab4c905ba675e08346ea7cb28b0e710c
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845502"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="0b84f-102">Postupy: Šifrování XML elementů pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="0b84f-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="0b84f-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování element v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0b84f-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="0b84f-104">Šifrování XML je standardní způsob pro výměnu nebo ukládání zašifrovaných dat XML, nemusíme mít starosti se snadno číst data.</span><span class="sxs-lookup"><span data-stu-id="0b84f-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="0b84f-105">Další informace o standardních šifrování XML, naleznete v tématu Specifikace World Wide Web Consortium (W3C) pro šifrování XML se nachází v <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="0b84f-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="0b84f-106">Vám pomůže šifrování XML nahradit všechny – element XML nebo dokument <`EncryptedData`> element, který obsahuje šifrovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="0b84f-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="0b84f-107"><`EncryptedData`> Element může obsahovat dílčí prvky, které obsahují informace o klíčích a procesy používané při šifrování.</span><span class="sxs-lookup"><span data-stu-id="0b84f-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="0b84f-108">Šifrování XML umožňuje dokument obsahovat několik elementů šifrované a umožňuje element, který má být zašifrovaný více než jednou.</span><span class="sxs-lookup"><span data-stu-id="0b84f-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="0b84f-109">Příklad kódu v tomto postupu se dozvíte, jak vytvořit <`EncryptedData`> element společně s několika dalšími dílčími elementy, které použijete později při dešifrování.</span><span class="sxs-lookup"><span data-stu-id="0b84f-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="0b84f-110">V tomto příkladu šifruje elementu XML s použitím dva klíče.</span><span class="sxs-lookup"><span data-stu-id="0b84f-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="0b84f-111">Vygeneruje certifikát X.509 test pomocí [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) a uloží certifikát do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="0b84f-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) and saves the certificate to a certificate store.</span></span>  <span data-ttu-id="0b84f-112">V příkladu potom programově načte příslušný certifikát a použije k zašifrování – element XML pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0b84f-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span>  <span data-ttu-id="0b84f-113">Interně <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda vytvoří oddělený klíč relace a použije k zašifrování dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0b84f-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="0b84f-114">Tato metoda zašifruje klíč relace a uloží ho spolu s šifrované XML v rámci nového <`EncryptedData`> element.</span><span class="sxs-lookup"><span data-stu-id="0b84f-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="0b84f-115">Chcete-li dešifrovat elementu XML, jednoduše zavolejte <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodu, která automaticky načte příslušný certifikát X.509 z úložiště a provede nezbytné dešifrování.</span><span class="sxs-lookup"><span data-stu-id="0b84f-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="0b84f-116">Další informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [postupy: dešifrování elementů XML pomocí certifikátů X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0b84f-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="0b84f-117">Tento příklad je vhodný pro situace, kdy je potřeba šifrovaná data sdílet více aplikací nebo pokud aplikace potřebuje k uložení šifrovaná data mezi časem, které běží.</span><span class="sxs-lookup"><span data-stu-id="0b84f-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="0b84f-118">K šifrování elementu XML pomocí certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="0b84f-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="0b84f-119">Použití [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) generovat testovacího certifikátu X.509 a umístěte ho do místního úložiště.</span><span class="sxs-lookup"><span data-stu-id="0b84f-119">Use the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) to generate a test X.509 certificate and place it in the local user store.</span></span>  <span data-ttu-id="0b84f-120">Budete muset vygenerovat klíč pro výměnu a je nutné provést klíč exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="0b84f-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="0b84f-121">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="0b84f-121">Run the following command:</span></span>  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  <span data-ttu-id="0b84f-122">Vytvoření <xref:System.Security.Cryptography.X509Certificates.X509Store> objektu a inicializovat ji a otevřete úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="0b84f-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  <span data-ttu-id="0b84f-123">Otevřete obchod v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="0b84f-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  <span data-ttu-id="0b84f-124">Inicializace <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> se všechny certifikáty v úložišti.</span><span class="sxs-lookup"><span data-stu-id="0b84f-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  <span data-ttu-id="0b84f-125">Zobrazit výčet prostřednictvím certifikáty v úložišti a najít certifikát s odpovídajícím názvem.</span><span class="sxs-lookup"><span data-stu-id="0b84f-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="0b84f-126">V tomto příkladu je název certifikátu `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="0b84f-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  <span data-ttu-id="0b84f-127">Zavřete ve storu, nebude tento certifikát je umístěn.</span><span class="sxs-lookup"><span data-stu-id="0b84f-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  <span data-ttu-id="0b84f-128">Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="0b84f-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="0b84f-129"><xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.</span><span class="sxs-lookup"><span data-stu-id="0b84f-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  <span data-ttu-id="0b84f-130">Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte nový <xref:System.Xml.XmlElement> objekt reprezentující element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="0b84f-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="0b84f-131">V tomto příkladu `"creditcard"` šifrovaná prvku.</span><span class="sxs-lookup"><span data-stu-id="0b84f-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="0b84f-132">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použít ho k zašifrování zadaného elementu pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="0b84f-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="0b84f-133"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda vrátí šifrovaný element jako <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.</span><span class="sxs-lookup"><span data-stu-id="0b84f-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="0b84f-134">Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.</span><span class="sxs-lookup"><span data-stu-id="0b84f-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="0b84f-135">Uložit <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="0b84f-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="0b84f-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b84f-136">Example</span></span>  
 <span data-ttu-id="0b84f-137">Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="0b84f-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="0b84f-138">Dále předpokládá, že `"test.xml"` obsahuje `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="0b84f-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="0b84f-139">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="0b84f-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b84f-140">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0b84f-140">Compiling the Code</span></span>  
  
-   <span data-ttu-id="0b84f-141">Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="0b84f-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="0b84f-142">Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="0b84f-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0b84f-143">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0b84f-143">.NET Framework Security</span></span>  
 <span data-ttu-id="0b84f-144">Certifikát X.509 použitý v tomto příkladu je pouze pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="0b84f-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="0b84f-145">Aplikace by měla použít certifikát X.509, který vygeneroval důvěryhodné certifikační autority nebo certifikát vytvořený certifikát serverem Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="0b84f-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b84f-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b84f-146">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="0b84f-147">Postupy: Dešifrování elementů XML pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="0b84f-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
