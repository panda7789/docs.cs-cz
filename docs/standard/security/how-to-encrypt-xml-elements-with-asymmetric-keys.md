---
title: 'Postupy: Šifrování elementů XML pomocí asymetrických klíčů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6840a9005aaca4805252298e1ceaf7e51f38971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Postupy: Šifrování elementů XML pomocí asymetrických klíčů
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro zašifrování element dokumentu XML.  XML – šifrování je standardní způsob, jak exchange nebo uložit šifrovaná data XML, bez starostí o data snadno čitelná.  Další informace o standardu šifrování XML, najdete v World Wide Web Consortium (W3C) specifikaci XML – šifrování v umístění http://www.w3.org/TR/xmldsig-core/.  
  
 XML – šifrování vám pomůže nahradit libovolný element, XML nebo dokument <`EncryptedData`> elementu, který obsahuje šifrovaná data XML.  <`EncryptedData`> Element může také obsahovat dílčí elementy, které obsahují informace o klíčích a postupech použitých při šifrování.  XML – šifrování umožňuje dokument obsahoval více šifrovaných elementů a umožňuje element k zašifrování vícekrát.  Příklad kódu v tomto postupu ukazuje postup vytvoření <`EncryptedData`> element společně s několika další dílčí prvky, které můžete použít později během dešifrování.  
  
 Tento příklad šifruje elementu XML s použitím dva klíče.  Generuje dvojici RSA veřejného a privátního klíče a uloží páru klíčů zabezpečeného kontejneru klíčů.  Tento příklad vytvoří oddělený klíč relace pomocí algoritmus Advanced Encryption (Standard AES), označované taky jako algoritmus Rijndael.  V příkladu používá klíč relace AES k šifrování dokumentu XML a pak používá k šifrování AES klíč relace veřejným klíčem RSA.  Nakonec příklad uloží zašifrovaný klíč relace a šifrovaná data XML v dokumentu XML v rámci nového <`EncryptedData`> elementu.  
  
 K dešifrování elementu XML, načtení privátního klíče RSA z kontejneru klíčů, použít ho k dešifrování klíče relace a pak použít klíč relace k dešifrování dokumentu.  Další informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [postupy: dešifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Tento příklad je vhodný pro situace, kdy je potřeba sdílet šifrovaná data více aplikací nebo pokud aplikace potřebuje k uložení šifrovaných dat v době mezi spuštěné.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>K zašifrování elementu XML asymetrickým klíčem  
  
1.  Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Generování symetrického klíče pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Klíč je automaticky uloží do kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> objektu do konstruktoru objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Tento klíč se použije k šifrování AES klíč relace a lze načíst později ho dešifrovat.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte novou <xref:System.Xml.XmlElement> objekt představující element, který chcete zašifrovat. V tomto příkladu `"creditcard"` je zašifrován element.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  Vytvoření nové relace klíče pomocí <xref:System.Security.Cryptography.RijndaelManaged> třídy.  Tento klíč bude šifrování elementu XML a pak se sám zašifrován a umístěny v dokumentu XML.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použít ho k zašifrování daného elementu pomocí klíče relace.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda vrací šifrovaný element jako pole bajtů šifrované.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  Vytvořit <xref:System.Security.Cryptography.Xml.EncryptedData> objektu a jeho naplnění identifikátor URL šifrovaného elementu XML.  Tento identifikátor URL umožňuje dešifrování objektu strany vědět, že soubor XML obsahuje element šifrované.  Můžete použít <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pole k určení identifikátoru adresy URL.  Nahradí element XML ve formátu prostého textu <`EncryptedData`> element zapouzdřené to <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  Vytvoření <xref:System.Security.Cryptography.Xml.EncryptionMethod> objekt, který je inicializován na identifikátor URL kryptografický algoritmus používaný k vygenerování klíče relace.  Předat <xref:System.Security.Cryptography.Xml.EncryptionMethod> do objektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> vlastnost.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedKey> objektu obsahuje šifrovaný klíč relace.  Šifrování klíče relace, přidejte ho do <xref:System.Security.Cryptography.Xml.EncryptedKey> objektu a zadejte název klíče relace a klíče identifikátoru adresy URL.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Vytvořte novou <xref:System.Security.Cryptography.Xml.DataReference> objekt, který mapuje šifrovaná data na určitý klíč relace.  Tento volitelný krok vám umožní snadno určit více částí dokumentu XML byly zašifrovaly jeden klíč.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Přidat šifrovaný klíč do <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Vytvořte novou <xref:System.Security.Cryptography.Xml.KeyInfo> objektu k zadání názvu klíče RSA.  Ho přidat do <xref:System.Security.Cryptography.Xml.EncryptedData> objektu. To pomáhá dešifrování objektu strany identifikovat správný asymetrický klíč používat k dešifrování klíče relace.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Přidat element šifrovaná data, která mají <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu s <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Uložit <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.  
  
-   Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy neukládají symetrický kryptografický klíč ve formátu prostého textu nebo přeneste symetrického klíče mezi počítači v podobě prostého textu.  Kromě toho nikdy uložení nebo přeneste privátní klíč pár asymetrických klíčů ve formátu prostého textu.  Další informace o symetrické a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy nevkládejte klíč přímo do zdrojového kódu.  Vložené klíče lze snadno přečíst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, například Poznámkový blok.  
  
 Po dokončení pomocí kryptografického klíče, vymazat z paměti nastavením všech bajtů na nulu nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda spravované kryptografické třídy.  Kryptografické klíče v některých případech můžete číst z paměti ladicí program nebo číst z pevného disku, pokud je stránkovaného umístění v paměti na disk.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography.Xml>  
 [Postupy: Dešifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
