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
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Postupy: Šifrování elementů XML pomocí certifikátů X.509

Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k zašifrování elementu v dokumentu XML.  Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.  Další informace o standardu šifrování XML naleznete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML v umístění <https://www.w3.org/TR/xmldsig-core/> .  
  
 Můžete použít šifrování XML k nahrazení libovolného elementu XML nebo dokumentu `EncryptedData` elementem <>, který obsahuje šifrovaná data XML. Prvek <`EncryptedData`> může obsahovat dílčí prvky, které obsahují informace o klíčích a procesech použitých při šifrování.  Šifrování XML umožňuje dokumentu obsahovat více šifrovaných prvků a umožňuje vícenásobné šifrování elementu.  Příklad kódu v tomto postupu ukazuje, jak vytvořit `EncryptedData` prvek <> spolu s několika dalšími dílčími prvky, které můžete použít později během dešifrování.  
  
Tento příklad šifruje XML element pomocí dvou klíčů. Příklad programově načte certifikát a použije ho k zašifrování XML elementu pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metody. Interně <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda vytvoří samostatný klíč relace a použije ho k zašifrování dokumentu XML. Tato metoda šifruje klíč relace a uloží jej spolu s šifrovaným XML v rámci nového <`EncryptedData`> elementu.  

Chcete-li dešifrovat XML element, zavolejte <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodu, která automaticky načte certifikát X. 509 z úložiště a provede nezbytné dešifrování.  Další informace o tom, jak dešifrovat XML element, který byl zašifrován pomocí tohoto postupu, naleznete v tématu [How to: Dešifrujte XML Elements pomocí certifikátů X. 509](how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Šifrování elementu XML pomocí certifikátu X. 509  

Chcete-li spustit tento příklad, musíte vytvořit testovací certifikát a uložit ho do úložiště certifikátů. Pokyny k této úloze jsou k dispozici pouze pro [Nástroj pro vytváření certifikátů systému Windows (Makecert.exe)](/windows/desktop/SecCrypto/makecert).

1. Pomocí [Makecert.exe](/windows/desktop/SecCrypto/makecert) vygenerujte testovací certifikát X. 509 a umístěte ho do úložiště místního uživatele. Musíte vygenerovat klíč pro výměnu a musíte si klíč exportovat. Spusťte následující příkaz:  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. Vytvořte <xref:System.Security.Cryptography.X509Certificates.X509Store> objekt a inicializujte ho pro otevření aktuálního úložiště uživatele.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. Otevřete Store v režimu jen pro čtení.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. Inicializujte <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> všechny certifikáty v úložišti.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. Zobrazte výčet certifikátů ve Storu a vyhledejte certifikát s příslušným názvem.  V tomto příkladu se certifikát jmenuje `"CN=XML_ENC_TEST_CERT"` .  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. Po umístění certifikátu zavřete úložiště.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. Vytvořte <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument>Objekt obsahuje element XML k zašifrování.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. Vyhledá zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvoří nový <xref:System.Xml.XmlElement> objekt, který reprezentuje element, který chcete zašifrovat.  V tomto příkladu `"creditcard"` je element zašifrovaný.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Vytvořte novou instanci <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použijte ji k zašifrování zadaného elementu pomocí certifikátu X. 509.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>Metoda vrátí zašifrovaný prvek jako <xref:System.Security.Cryptography.Xml.EncryptedData> objekt.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Nahraďte element z původního <xref:System.Xml.XmlDocument> objektu <xref:System.Security.Cryptography.Xml.EncryptedData> elementem.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Uložte <xref:System.Xml.XmlDocument> objekt.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se předpokládá, že soubor s názvem `"test.xml"` existuje ve stejném adresáři jako kompilovaný program.  Také předpokládá, že `"test.xml"` obsahuje `"creditcard"` element.  Následující kód XML můžete umístit do souboru s názvem `test.xml` a použít ho v tomto příkladu.  
  
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
  
- V projektu, který cílí na .NET Framework, zahrňte odkaz na `System.Security.dll` .

- V projektu, který cílí na .NET Core nebo .NET 5, nainstalujte balíček NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).
  
- Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-security"></a>Zabezpečení .NET
  
Certifikát X. 509 použitý v tomto příkladu je určen pouze pro testovací účely.  Aplikace by měly používat certifikát X. 509 generovaný důvěryhodnou certifikační autoritou.  
  
## <a name="see-also"></a>Viz také

- [Kryptografický model](cryptography-model.md)
- [Šifrovací služby](cryptographic-services.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [Postupy: Dešifrování elementů XML pomocí certifikátů X.509](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
