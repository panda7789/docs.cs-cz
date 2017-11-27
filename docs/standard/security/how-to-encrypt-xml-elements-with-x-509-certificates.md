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
ms.openlocfilehash: 6690c87bb7a632a783fc89341d405bf81166470c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Postupy: Šifrování XML elementů pomocí certifikátů X.509
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro zašifrování element dokumentu XML.  XML – šifrování je standardní způsob, jak exchange nebo uložit šifrovaná data XML, bez starostí o data snadno čitelná.  Další informace o standardu šifrování XML najdete v článku, že specifikace World Wide Web Consortium (W3C) pro šifrování XML nacházející se v http://www.w3.org/TR/xmldsig-core/.  
  
 XML – šifrování vám pomůže nahradit libovolný element, XML nebo dokument <`EncryptedData`> elementu, který obsahuje šifrovaná data XML. <`EncryptedData`> Element může obsahovat dílčí elementy, které obsahují informace o klíčích a postupech použitých při šifrování.  XML – šifrování umožňuje dokument obsahoval více šifrovaných elementů a umožňuje element k zašifrování vícekrát.  Příklad kódu v tomto postupu se dozvíte, jak vytvořit <`EncryptedData`> element společně s několika další dílčí prvky, které můžete použít později během dešifrování.  
  
 Tento příklad šifruje elementu XML s použitím dva klíče.  Vygeneruje testovací certifikát X.509 pomocí [nástroje vytvoření certifikátu (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) a ukládá certifikát do úložiště certifikátů.  V příkladu pak prostřednictvím kódu programu načte příslušný certifikát a použije ho k zašifrování elementu XML pomocí <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda.  Interně <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda vytvoří oddělený klíč relace a použije ho k zašifrování dokumentu XML. Tato metoda zašifruje klíč relace a uloží spolu s šifrované XML v rámci nového <`EncryptedData`> elementu.  
  
 K dešifrování elementu XML, stačí zavolat <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda, která automaticky načte certifikát X.509 z úložiště a provede nezbytné dešifrování.  Další informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [postupy: dešifrování XML elementů pomocí certifikátů X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 Tento příklad je vhodný pro situace, kdy je potřeba sdílet šifrovaná data více aplikací nebo pokud aplikace potřebuje k uložení šifrovaných dat v době mezi spuštěné.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>K šifrování XML element společně s certifikátem X.509  
  
1.  Použití [nástroje vytvoření certifikátu (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) generovat testovacího certifikátu X.509 a umístěte jej do úložiště místního uživatele.  Musíte vygenerovat klíč pro výměnu a je nutné provést klíč jako exportovatelný. Spusťte následující příkaz:  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  Vytvoření <xref:System.Security.Cryptography.X509Certificates.X509Store> objektu a inicializace otevřete úložiště aktuálního uživatele.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  Otevřete úložiště v režimu jen pro čtení.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  Inicializace <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> se všechny certifikáty v úložišti.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  Projděte certifikáty v úložišti a najít certifikát s odpovídající název.  V tomto příkladu je certifikát s názvem `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  Zavřete se nachází úložiště po certifikát.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte novou <xref:System.Xml.XmlElement> objekt představující element, který chcete zašifrovat.  V tomto příkladu `"creditcard"` je zašifrován element.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použít ho k zašifrování zadaného elementu pomocí certifikátu X.509.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda vrátí šifrované prvek jako <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu s <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Uložit <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.  
  
-   Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Certifikát X.509 použité v tomto příkladu je pouze pro účely testování.  Aplikace by měl použít certifikát X.509 generované důvěryhodné certifikační autority nebo certifikát vytvořený certifikační Server Microsoft Windows.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography.Xml>  
 [Postupy: dešifrování XML elementů pomocí certifikátů X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
