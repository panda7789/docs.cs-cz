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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25a2fb441269508402263e103a6c6e1be2635406
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869521"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Postupy: Dešifrování XML elementů pomocí certifikátů X.509
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování a dešifrování element v dokumentu XML.  Šifrování XML je standardní způsob pro výměnu nebo ukládání zašifrovaných dat XML, nemusíme mít starosti se snadno číst data.  Další informace o standardních šifrování XML, naleznete v tématu Specifikace World Wide Web Consortium (W3C) pro šifrování XML se nachází v http://www.w3.org/TR/xmldsig-core/.  
  
 Dešifruje elementu XML, který byl zašifrován pomocí metod popsaných v tomto příkladu: [postupy: šifrování elementů XML pomocí certifikátů X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).  Najde <`EncryptedData`> element, dešifruje element a element nahradí původní element XML ve formátu prostého textu.  
  
 Příklad kódu v tomto postupu dešifruje elementu XML pomocí certifikátu X.509 z místního úložiště certifikátů aktuálního uživatelského účtu.  V příkladu se používá <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda automaticky načíst certifikát X.509 a dešifrování klíče uloženého v relaci <`EncryptedKey`> element <`EncryptedData`> element.  <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Metoda automaticky použije klíč relace k dešifrování XML element.  
  
 Tento příklad je vhodný pro situace, kdy je potřeba šifrovaná data sdílet více aplikací nebo pokud aplikace potřebuje k uložení šifrovaná data mezi časem, které běží.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>Dešifrování elementu XML pomocí certifikátu X.509  
  
1.  Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje element XML k dešifrování.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  Vytvořte nový <xref:System.Security.Cryptography.Xml.EncryptedXml> objekt tím, že předáte <xref:System.Xml.XmlDocument> objekt konstruktoru.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  Dešifrování pomocí dokumentu XML <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  Uložit <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>Příklad  
 Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.  Dále předpokládá, že `"test.xml"` obsahuje `"creditcard"` elementu.  Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.  
  
-   Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Certifikát X.509 použitý v tomto příkladu je pouze pro účely testování.  Aplikace by měla použít certifikát X.509, který vygeneroval důvěryhodné certifikační autority nebo certifikát vytvořený certifikát serverem Microsoft Windows.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>  
- [Postupy: Šifrování elementů XML pomocí certifikátů X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
