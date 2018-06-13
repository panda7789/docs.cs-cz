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
ms.openlocfilehash: 0064aaf2e67eb3fb40e4c58995ce8678321d21aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583328"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Postupy: Dešifrování XML elementů pomocí certifikátů X.509
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování a dešifrování element dokumentu XML.  XML – šifrování je standardní způsob, jak exchange nebo uložit šifrovaná data XML, bez starostí o data snadno čitelná.  Další informace o standardu šifrování XML, najdete v World Wide Web Consortium (W3C) specifikaci XML – šifrování v umístění http://www.w3.org/TR/xmldsig-core/.  
  
 Dešifruje element XML, který byl zašifrován pomocí metody popsané v tomto příkladu: [postupy: šifrování XML elementů pomocí certifikátů X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).  Najde <`EncryptedData`> elementu, element dešifruje a element nahradí původní element XML ve formátu prostého textu.  
  
 Příklad kódu v tomto postupu dešifruje element XML pomocí certifikátu X.509. certifikát z místního úložiště certifikátů aktuálního uživatelského účtu.  V příkladu se používá <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda k automatickému načtení certifikátu X.509 a dešifrování klíče uloženého v relaci <`EncryptedKey`> elementu <`EncryptedData`> elementu.  <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Metoda pak automaticky používá klíč relace k dešifrování elementu XML.  
  
 Tento příklad je vhodný pro situace, kdy je potřeba sdílet šifrovaná data více aplikací nebo pokud aplikace potřebuje k uložení šifrovaných dat v době mezi spuštěné.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>K dešifrování XML element společně s certifikátem X.509  
  
1.  Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje element XML k dešifrování.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  Vytvořte novou <xref:System.Security.Cryptography.Xml.EncryptedXml> objekt předáním <xref:System.Xml.XmlDocument> objekt konstruktoru.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  Dešifrování dokument XML pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  Uložit <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>Příklad  
 Tento příklad předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako zkompilovaný program.  Dále předpokládá, že `"test.xml"` obsahuje `"creditcard"` elementu.  Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít jej v tomto příkladu.  
  
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
  
-   Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.  
  
-   Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Certifikát X.509 použité v tomto příkladu je pouze pro účely testování.  Aplikace by měl použít certifikát X.509 generované důvěryhodné certifikační autority nebo certifikát vytvořený certifikační Server Microsoft Windows.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography.Xml>  
 [Postupy: Šifrování elementů XML pomocí certifikátů X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
