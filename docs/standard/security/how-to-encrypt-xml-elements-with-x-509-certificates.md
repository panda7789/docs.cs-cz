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
ms.openlocfilehash: 060bc53efa175314e00f487776c43124c39f33c0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970971"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Postupy: Šifrování XML elementů pomocí certifikátů X.509
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování element v dokumentu XML.  Šifrování XML je standardní způsob pro výměnu nebo ukládání zašifrovaných dat XML, nemusíme mít starosti se snadno číst data.  Další informace o standardních šifrování XML, naleznete v tématu Specifikace World Wide Web Consortium (W3C) pro šifrování XML se nachází v <https://www.w3.org/TR/xmldsig-core/>.  
  
 Vám pomůže šifrování XML nahradit všechny – element XML nebo dokument <`EncryptedData`> element, který obsahuje šifrovaná data XML. <`EncryptedData`> Element může obsahovat dílčí prvky, které obsahují informace o klíčích a procesy používané při šifrování.  Šifrování XML umožňuje dokument obsahovat několik elementů šifrované a umožňuje element, který má být zašifrovaný více než jednou.  Příklad kódu v tomto postupu se dozvíte, jak vytvořit <`EncryptedData`> element společně s několika dalšími dílčími elementy, které použijete později při dešifrování.  
  
 V tomto příkladu šifruje elementu XML s použitím dva klíče. Vygeneruje certifikát X.509 test pomocí [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) a uloží certifikát do úložiště certifikátů. V příkladu potom programově načte příslušný certifikát a použije k zašifrování – element XML pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metody. Interně <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda vytvoří oddělený klíč relace a použije k zašifrování dokumentu XML. Tato metoda zašifruje klíč relace a uloží ho spolu s šifrované XML v rámci nového <`EncryptedData`> element.  
  
 Chcete-li dešifrovat elementu XML, jednoduše zavolejte <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodu, která automaticky načte příslušný certifikát X.509 z úložiště a provede nezbytné dešifrování.  Další informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [jak: Dešifrování elementů XML pomocí certifikátů X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 Tento příklad je vhodný pro situace, kdy je potřeba šifrovaná data sdílet více aplikací nebo pokud aplikace potřebuje k uložení šifrovaná data mezi časem, které běží.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>K šifrování elementu XML pomocí certifikátu X.509  
  
1.  Použití [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) generovat testovacího certifikátu X.509 a umístěte ho do místního úložiště.  Budete muset vygenerovat klíč pro výměnu a je nutné provést klíč exportovatelné. Spusťte následující příkaz:  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  Vytvoření <xref:System.Security.Cryptography.X509Certificates.X509Store> objektu a inicializovat ji a otevřete úložiště pro aktuálního uživatele.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  Otevřete obchod v režimu jen pro čtení.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  Inicializace <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> se všechny certifikáty v úložišti.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  Zobrazit výčet prostřednictvím certifikáty v úložišti a najít certifikát s odpovídajícím názvem.  V tomto příkladu je název certifikátu `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  Zavřete ve storu, nebude tento certifikát je umístěn.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte nový <xref:System.Xml.XmlElement> objekt reprezentující element, který chcete zašifrovat.  V tomto příkladu `"creditcard"` šifrovaná prvku.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použít ho k zašifrování zadaného elementu pomocí certifikátu X.509.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda vrátí šifrovaný element jako <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Uložit <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.  
  
-   Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Certifikát X.509 použitý v tomto příkladu je pouze pro účely testování.  Aplikace by měla použít certifikát X.509, který vygeneroval důvěryhodné certifikační autority nebo certifikát vytvořený certifikát serverem Microsoft Windows.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Dešifrování elementů XML pomocí certifikátů X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
