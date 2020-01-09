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
ms.openlocfilehash: 46fbefbf7a427ec0d60a34ecc2166f8499d08575
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708885"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Postupy: Dešifrování XML elementů pomocí certifikátů X.509
Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování a dešifrování elementu v dokumentu XML.  Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.  Další informace o standardu šifrování XML najdete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML umístěné v <https://www.w3.org/TR/xmldsig-core/>.  
  
 Tento příklad dešifruje XML element, který byl zašifrován pomocí metod popsaných v tématu: [Postupy: šifrování elementů XML pomocí certifikátů X. 509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).  Najde <`EncryptedData`> element, dešifruje prvek a pak nahradí element původním nešifrovaným XML elementem.  
  
 Příklad kódu v tomto postupu dešifruje XML element pomocí certifikátu X. 509 z místního úložiště certifikátů aktuálního uživatelského účtu.  V příkladu se používá metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> k automatickému načtení certifikátu X. 509 a dešifruje klíč relace uložený v <`EncryptedKey`prvek > prvku <`EncryptedData`> elementu.  Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> pak automaticky použije klíč relace k dešifrování XML elementu.  
  
 Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>Dešifrování elementu XML pomocí certifikátu X. 509  
  
1. Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.  Objekt <xref:System.Xml.XmlDocument> obsahuje element XML k dešifrování.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. Vytvořte nový objekt <xref:System.Security.Cryptography.Xml.EncryptedXml> předáním objektu <xref:System.Xml.XmlDocument> do konstruktoru.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. Dešifrujte dokument XML pomocí metody <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. Uložte objekt <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.  Předpokládá také, že `"test.xml"` obsahuje `"creditcard"` prvek.  Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.  
  
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
  
- Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.  
  
- Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Certifikát X. 509 použitý v tomto příkladu je určen pouze pro testovací účely.  Aplikace by měly používat certifikát X. 509 vygenerovaný důvěryhodnou certifikační autoritou nebo používat certifikát vygenerovaný serverem Microsoft Windows Certificate Server.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Šifrování elementů XML pomocí certifikátů X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
