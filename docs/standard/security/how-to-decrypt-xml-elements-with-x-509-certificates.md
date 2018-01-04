---
title: "Postupy: Dešifrování XML elementů pomocí certifikátů X.509"
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
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c922b3da772c685343b8989c5dc1bc89cad857fd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="f5114-102">Postupy: Dešifrování XML elementů pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="f5114-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="f5114-103">Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování a dešifrování element dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f5114-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="f5114-104">XML – šifrování je standardní způsob, jak exchange nebo uložit šifrovaná data XML, bez starostí o data snadno čitelná.</span><span class="sxs-lookup"><span data-stu-id="f5114-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="f5114-105">Další informace o standardu šifrování XML najdete v článku, že specifikace World Wide Web Consortium (W3C) pro šifrování XML nacházející se v http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="f5114-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="f5114-106">Dešifruje element XML, který byl zašifrován pomocí metody popsané v tomto příkladu: [postupy: šifrování XML elementů pomocí certifikátů X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f5114-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="f5114-107">Najde <`EncryptedData`> elementu, element dešifruje a element nahradí původní element XML ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="f5114-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="f5114-108">Příklad kódu v tomto postupu dešifruje element XML pomocí certifikátu X.509. certifikát z místního úložiště certifikátů aktuálního uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="f5114-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="f5114-109">V příkladu se používá <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda k automatickému načtení certifikátu X.509 a dešifrování klíče uloženého v relaci <`EncryptedKey`> elementu <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="f5114-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="f5114-110"><xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Metoda pak automaticky používá klíč relace k dešifrování elementu XML.</span><span class="sxs-lookup"><span data-stu-id="f5114-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="f5114-111">Tento příklad je vhodný pro situace, kdy je potřeba sdílet šifrovaná data více aplikací nebo pokud aplikace potřebuje k uložení šifrovaných dat v době mezi spuštěné.</span><span class="sxs-lookup"><span data-stu-id="f5114-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="f5114-112">K dešifrování XML element společně s certifikátem X.509</span><span class="sxs-lookup"><span data-stu-id="f5114-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="f5114-113">Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.</span><span class="sxs-lookup"><span data-stu-id="f5114-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="f5114-114"><xref:System.Xml.XmlDocument> Objekt obsahuje element XML k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="f5114-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="f5114-115">Vytvořte novou <xref:System.Security.Cryptography.Xml.EncryptedXml> objekt předáním <xref:System.Xml.XmlDocument> objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f5114-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="f5114-116">Dešifrování dokument XML pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f5114-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="f5114-117">Uložit <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="f5114-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="f5114-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5114-118">Example</span></span>  
 <span data-ttu-id="f5114-119">Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="f5114-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="f5114-120">Dále předpokládá, že `"test.xml"` obsahuje `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="f5114-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="f5114-121">Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít jej v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="f5114-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5114-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f5114-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f5114-123">Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="f5114-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="f5114-124">Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="f5114-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f5114-125">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f5114-125">.NET Framework Security</span></span>  
 <span data-ttu-id="f5114-126">Certifikát X.509 použité v tomto příkladu je pouze pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="f5114-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="f5114-127">Aplikace by měl použít certifikát X.509 generované důvěryhodné certifikační autority nebo certifikát vytvořený certifikační Server Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="f5114-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5114-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5114-128">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="f5114-129">Postupy: Šifrování elementů XML pomocí certifikátů X.509</span><span class="sxs-lookup"><span data-stu-id="f5114-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
