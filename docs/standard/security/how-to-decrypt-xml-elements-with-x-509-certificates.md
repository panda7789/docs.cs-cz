---
title: 'Postupy: Dešifrování XML elementů pomocí certifikátů X.509'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
ms.openlocfilehash: 32a6d95b96bb20571c14c16cc70b944fa3e4032b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277385"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="85ff1-102">Postupy: Dešifrování XML elementů pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="85ff1-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="85ff1-103">Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k zašifrování a dešifrování elementu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="85ff1-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="85ff1-104">Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.</span><span class="sxs-lookup"><span data-stu-id="85ff1-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="85ff1-105">Další informace o standardu šifrování XML naleznete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML v umístění <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="85ff1-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="85ff1-106">Tento příklad dešifruje XML element, který byl zašifrován pomocí metod popsaných v tématu: [Postupy: šifrování elementů XML pomocí certifikátů X. 509](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="85ff1-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="85ff1-107">Najde <`EncryptedData`> prvek, dešifruje prvek a poté nahradí element původním nešifrovaným elementem XML.</span><span class="sxs-lookup"><span data-stu-id="85ff1-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="85ff1-108">Příklad kódu v tomto postupu dešifruje XML element pomocí certifikátu X. 509 z místního úložiště certifikátů aktuálního uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="85ff1-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="85ff1-109">V příkladu se používá <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Metoda k automatickému načtení certifikátu X. 509 a dešifrování klíče relace uloženého v prvku <`EncryptedKey`> elementu <ho `EncryptedData`>.</span><span class="sxs-lookup"><span data-stu-id="85ff1-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="85ff1-110"><xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>Metoda pak automaticky použije klíč relace k dešifrování elementu XML.</span><span class="sxs-lookup"><span data-stu-id="85ff1-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="85ff1-111">Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.</span><span class="sxs-lookup"><span data-stu-id="85ff1-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="85ff1-112">Dešifrování elementu XML pomocí certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="85ff1-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="85ff1-113">Vytvořte <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="85ff1-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="85ff1-114"><xref:System.Xml.XmlDocument>Objekt obsahuje element XML k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="85ff1-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <span data-ttu-id="85ff1-115">Vytvořte nový <xref:System.Security.Cryptography.Xml.EncryptedXml> objekt předáním <xref:System.Xml.XmlDocument> objektu do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="85ff1-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <span data-ttu-id="85ff1-116">Dešifrujte dokument XML pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="85ff1-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <span data-ttu-id="85ff1-117">Uložte <xref:System.Xml.XmlDocument> objekt.</span><span class="sxs-lookup"><span data-stu-id="85ff1-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="85ff1-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="85ff1-118">Example</span></span>  
 <span data-ttu-id="85ff1-119">V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="85ff1-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="85ff1-120">Také předpokládá, že `"test.xml"` obsahuje `"creditcard"` element.</span><span class="sxs-lookup"><span data-stu-id="85ff1-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="85ff1-121">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="85ff1-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85ff1-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="85ff1-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="85ff1-123">Chcete-li tento příklad zkompilovat, je nutné zahrnout odkaz na `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="85ff1-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="85ff1-124">Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="85ff1-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="85ff1-125">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="85ff1-125">.NET Framework Security</span></span>  
 <span data-ttu-id="85ff1-126">Certifikát X. 509 použitý v tomto příkladu je určen pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="85ff1-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="85ff1-127">Aplikace by měly používat certifikát X. 509 vygenerovaný důvěryhodnou certifikační autoritou nebo používat certifikát vygenerovaný serverem Microsoft Windows Certificate Server.</span><span class="sxs-lookup"><span data-stu-id="85ff1-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ff1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="85ff1-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="85ff1-129">Postupy: Šifrování elementů XML pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="85ff1-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](how-to-encrypt-xml-elements-with-x-509-certificates.md)
