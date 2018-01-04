---
title: "Postupy: Šifrování XML elementů pomocí certifikátů X.509"
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
- encryption [.NET Framework], X.509 certificates
- cryptography [.NET Framework], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 108a07a818adaec6734637da2c95aed42e837847
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="6c5c4-102">Postupy: Šifrování XML elementů pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="6c5c4-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="6c5c4-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro zašifrování element dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="6c5c4-104">XML – šifrování je standardní způsob, jak exchange nebo uložit šifrovaná data XML, bez starostí o data snadno čitelná.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="6c5c4-105">Další informace o standardu šifrování XML najdete v článku, že specifikace World Wide Web Consortium (W3C) pro šifrování XML nacházející se v http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="6c5c4-106">XML – šifrování vám pomůže nahradit libovolný element, XML nebo dokument <`EncryptedData`> elementu, který obsahuje šifrovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="6c5c4-107"><`EncryptedData`> Element může obsahovat dílčí elementy, které obsahují informace o klíčích a postupech použitých při šifrování.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="6c5c4-108">XML – šifrování umožňuje dokument obsahoval více šifrovaných elementů a umožňuje element k zašifrování vícekrát.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="6c5c4-109">Příklad kódu v tomto postupu se dozvíte, jak vytvořit <`EncryptedData`> element společně s několika další dílčí prvky, které můžete použít později během dešifrování.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="6c5c4-110">Tento příklad šifruje elementu XML s použitím dva klíče.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="6c5c4-111">Vygeneruje testovací certifikát X.509 pomocí [nástroje vytvoření certifikátu (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) a ukládá certifikát do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) and saves the certificate to a certificate store.</span></span>  <span data-ttu-id="6c5c4-112">V příkladu pak prostřednictvím kódu programu načte příslušný certifikát a použije ho k zašifrování elementu XML pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span>  <span data-ttu-id="6c5c4-113">Interně <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda vytvoří oddělený klíč relace a použije ho k zašifrování dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="6c5c4-114">Tato metoda zašifruje klíč relace a uloží spolu s šifrované XML v rámci nového <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="6c5c4-115">K dešifrování elementu XML, stačí zavolat <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda, která automaticky načte certifikát X.509 z úložiště a provede nezbytné dešifrování.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="6c5c4-116">Další informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [postupy: dešifrování XML elementů pomocí certifikátů X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6c5c4-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="6c5c4-117">Tento příklad je vhodný pro situace, kdy je potřeba sdílet šifrovaná data více aplikací nebo pokud aplikace potřebuje k uložení šifrovaných dat v době mezi spuštěné.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="6c5c4-118">K šifrování XML element společně s certifikátem X.509</span><span class="sxs-lookup"><span data-stu-id="6c5c4-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="6c5c4-119">Použití [nástroje vytvoření certifikátu (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) generovat testovacího certifikátu X.509 a umístěte jej do úložiště místního uživatele.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-119">Use the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) to generate a test X.509 certificate and place it in the local user store.</span></span>  <span data-ttu-id="6c5c4-120">Musíte vygenerovat klíč pro výměnu a je nutné provést klíč jako exportovatelný.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="6c5c4-121">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="6c5c4-121">Run the following command:</span></span>  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  <span data-ttu-id="6c5c4-122">Vytvoření <xref:System.Security.Cryptography.X509Certificates.X509Store> objektu a inicializace otevřete úložiště aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  <span data-ttu-id="6c5c4-123">Otevřete úložiště v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  <span data-ttu-id="6c5c4-124">Inicializace <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> se všechny certifikáty v úložišti.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  <span data-ttu-id="6c5c4-125">Projděte certifikáty v úložišti a najít certifikát s odpovídající název.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="6c5c4-126">V tomto příkladu je certifikát s názvem `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  <span data-ttu-id="6c5c4-127">Zavřete se nachází úložiště po certifikát.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  <span data-ttu-id="6c5c4-128">Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="6c5c4-129"><xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  <span data-ttu-id="6c5c4-130">Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte novou <xref:System.Xml.XmlElement> objekt představující element, který chcete zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="6c5c4-131">V tomto příkladu `"creditcard"` je zašifrován element.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="6c5c4-132">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použít ho k zašifrování zadaného elementu pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="6c5c4-133"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda vrátí šifrované prvek jako <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="6c5c4-134">Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu s <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="6c5c4-135">Uložit <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="6c5c4-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c5c4-136">Example</span></span>  
 <span data-ttu-id="6c5c4-137">Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="6c5c4-138">Dále předpokládá, že `"test.xml"` obsahuje `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="6c5c4-139">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít jej v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c5c4-140">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6c5c4-140">Compiling the Code</span></span>  
  
-   <span data-ttu-id="6c5c4-141">Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="6c5c4-142">Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6c5c4-143">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6c5c4-143">.NET Framework Security</span></span>  
 <span data-ttu-id="6c5c4-144">Certifikát X.509 použité v tomto příkladu je pouze pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="6c5c4-145">Aplikace by měl použít certifikát X.509 generované důvěryhodné certifikační autority nebo certifikát vytvořený certifikační Server Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="6c5c4-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c5c4-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c5c4-146">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="6c5c4-147">Postupy: Dešifrování elementů XML pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="6c5c4-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
