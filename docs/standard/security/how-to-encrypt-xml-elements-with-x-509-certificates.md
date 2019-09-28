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
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Postupy: Šifrování elementů XML pomocí certifikátů X.509
Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování elementu v dokumentu XML.  Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.  Další informace o standardu šifrování XML najdete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML umístěné na <https://www.w3.org/TR/xmldsig-core/>.  
  
 Můžete použít šifrování XML k nahrazení libovolného elementu XML nebo dokumentu pomocí < elementu `EncryptedData` >, který obsahuje šifrovaná data XML. < Element `EncryptedData` > může obsahovat dílčí prvky, které obsahují informace o klíčích a procesech použitých při šifrování.  Šifrování XML umožňuje dokumentu obsahovat více šifrovaných prvků a umožňuje vícenásobné šifrování elementu.  Příklad kódu v tomto postupu ukazuje, jak vytvořit < prvek `EncryptedData` > spolu s několika dalšími dílčími prvky, které můžete použít později během dešifrování.  
  
 Tento příklad šifruje XML element pomocí dvou klíčů. Vygeneruje testovací certifikát X. 509 pomocí nástroje pro [Vytvoření certifikátu (Makecert. exe)](/windows/desktop/SecCrypto/makecert) a uloží certifikát do úložiště certifikátů. Příklad následně programově načte certifikát a použije ho k zašifrování XML elementu pomocí metody <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>. Interně metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> vytvoří samostatný klíč relace a použije ho k zašifrování dokumentu XML. Tato metoda šifruje klíč relace a uloží jej spolu s šifrovaným XML v rámci nového < elementu `EncryptedData` >.  
  
 Chcete-li dešifrovat XML element, jednoduše zavolejte metodu <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>, která automaticky načte certifikát X. 509 z úložiště a provede nezbytné dešifrování.  Další informace o tom, jak dešifrovat XML element, který byl zašifrovaný pomocí tohoto postupu, naleznete v tématu [How na: Dešifrování elementů XML pomocí certifikátů X. 509 @ no__t-0.  
  
 Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Šifrování elementu XML pomocí certifikátu X. 509  
  
1. Pomocí [Nástroje pro tvorbu certifikátů (Makecert. exe)](/windows/desktop/SecCrypto/makecert) vygenerujte testovací certifikát X. 509 a umístěte ho do úložiště místního uživatele. Musíte vygenerovat klíč pro výměnu a musíte si klíč exportovat. Spusťte následující příkaz:  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. Vytvořit objekt <xref:System.Security.Cryptography.X509Certificates.X509Store> a inicializovat ho pro otevření aktuálního úložiště uživatele.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. Otevřete Store v režimu jen pro čtení.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. Inicializujte <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> se všemi certifikáty v úložišti.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. Zobrazte výčet certifikátů ve Storu a vyhledejte certifikát s příslušným názvem.  V tomto příkladu je certifikát nazvaný `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. Po umístění certifikátu zavřete úložiště.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.  Objekt <xref:System.Xml.XmlDocument> obsahuje element XML, který se má zašifrovat.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. Vyhledá zadaný element v objektu @no__t 0 a vytvoří nový objekt <xref:System.Xml.XmlElement>, který reprezentuje element, který chcete zašifrovat.  V tomto příkladu je prvek `"creditcard"` zašifrovaný.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Vytvořte novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> a použijte ji k zašifrování zadaného elementu pomocí certifikátu X. 509.  Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> vrátí šifrovaný element jako objekt <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Nahraďte prvek z původního objektu <xref:System.Xml.XmlDocument> pomocí elementu <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Uložte objekt <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.  Také předpokládá, že `"test.xml"` obsahuje prvek `"creditcard"`.  Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.  
  
- Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Certifikát X. 509 použitý v tomto příkladu je určen pouze pro testovací účely.  Aplikace by měly používat certifikát X. 509 vygenerovaný důvěryhodnou certifikační autoritou nebo používat certifikát vygenerovaný serverem Microsoft Windows Certificate Server.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Dešifrování elementů XML pomocí certifikátů X. 509 @ no__t-0
