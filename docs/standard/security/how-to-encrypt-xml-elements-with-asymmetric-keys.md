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
ms.openlocfilehash: 61984d4778e42abf378a1369a86ba599d78980af
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121321"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Postupy: Šifrování elementů XML pomocí asymetrických klíčů
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování element v dokumentu XML.  Šifrování XML je standardní způsob pro výměnu nebo ukládání zašifrovaných dat XML, nemusíme mít starosti se snadno číst data.  Další informace o standardních šifrování XML, naleznete v tématu Specifikace World Wide Web Consortium (W3C) pro šifrování XML se nachází v <https://www.w3.org/TR/xmldsig-core/>.  
  
 Vám pomůže šifrování XML nahradit všechny – element XML nebo dokument <`EncryptedData`> element, který obsahuje šifrovaná data XML.  <`EncryptedData`> Element může také obsahovat dílčí prvky, které obsahují informace o klíčích a procesy používané při šifrování.  Šifrování XML umožňuje dokument obsahovat několik elementů šifrované a umožňuje element, který má být zašifrovaný více než jednou.  Příklad kódu v tomto postupu ukazuje, jak vytvořit <`EncryptedData`> element společně s několika dalšími dílčími elementy, které použijete později při dešifrování.  
  
 V tomto příkladu šifruje elementu XML s použitím dva klíče.  Generuje pár veřejného a privátního klíče RSA a uloží pár klíčů zabezpečeného kontejneru klíčů.  Příklad poté vytvoří samostatné relaci klíče pomocí algoritmus Advanced Encryption (Standard AES), také nazývané algoritmu Rijndael.  V příkladu používá klíč relace AES pro šifrování dokumentů XML a pak pomocí veřejného klíče RSA pro šifrování s klíčem relace AES.  Nakonec příklad uloží zašifrovaný klíč relace a šifrovaná data XML v dokumentu XML v rámci nového <`EncryptedData`> element.  
  
 K dešifrování elementu XML, načíst privátní klíč RSA v kontejneru klíčů, použít ho k dešifrování klíče relace a pak použít klíč relace k dešifrování dokumentu.  Další informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [postupy: dešifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Tento příklad je vhodný pro situace, kdy je potřeba šifrovaná data sdílet více aplikací nebo pokud aplikace potřebuje k uložení šifrovaná data mezi časem, které běží.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>K šifrování platný element XML s asymetrický klíč  
  
1.  Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Vygenerovat symetrický klíč pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Klíč se automaticky uloží do kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy.  Tento klíč se použije k šifrování s klíčem relace AES a lze načíst později je dešifrovat.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte nový <xref:System.Xml.XmlElement> objekt reprezentující element, který chcete zašifrovat. V tomto příkladu `"creditcard"` šifrovaná prvku.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  Vytvořit novou relaci klíče pomocí <xref:System.Security.Cryptography.RijndaelManaged> třídy.  Tento klíč bude šifrování elementu XML a pak se sám zašifrován a umístěny v dokumentu XML.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a použít ho k zašifrování zadaného elementu pomocí klíče relace.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda vrátí šifrovaný element jako pole šifrovaných bajtů.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedData> objektu a jeho naplnění identifikátor URL šifrovaný element XML.  Tento identifikátor URL umožňuje dešifrování strana vědět, že kód XML obsahuje šifrovaný element.  Můžete použít <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pole k určení identifikátoru adresy URL.  Element XML ve formátu prostého textu se nahradí <`EncryptedData`> element zapouzdřené situace <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  Vytvoření <xref:System.Security.Cryptography.Xml.EncryptionMethod> , který je inicializován na identifikátor URL kryptografický algoritmus používaný ke generování klíče relace.  Předání <xref:System.Security.Cryptography.Xml.EncryptionMethod> objektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> vlastnost.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedKey> objektu tak, aby obsahovala šifrovaný klíč relace.  Šifrování klíče relace, přidejte ji tak <xref:System.Security.Cryptography.Xml.EncryptedKey> objektu a zadejte název klíče relace a klíče identifikátoru adresy URL.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Vytvořte nový <xref:System.Security.Cryptography.Xml.DataReference> objekt, který mapuje šifrovaná data na určitý klíč relace.  Tento krok vám umožní snadno určit více částí dokumentu XML bylo zašifrováno jeden klíč.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Šifrovaný klíč k přidání <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Vytvořte nový <xref:System.Security.Cryptography.Xml.KeyInfo> objektu k zadání názvu klíče RSA.  Přidejte ji tak <xref:System.Security.Cryptography.Xml.EncryptedData> objektu. To pomáhá dešifrování stran identifikovat správné asymetrický klíč používat k dešifrování klíče relace.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Přidat data šifrovaný element <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Uložit <xref:System.Xml.XmlDocument> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.  
  
-   Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy ukládat symetrický šifrovací klíč ve formátu prostého textu nebo přenášet symetrického klíče mezi počítači ve formátu prostého textu.  Kromě toho nikdy ukládat nebo přenášet privátní klíč pro pár asymetrických klíčů ve formátu prostého textu.  Další informace o symetrický a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Klíč pro vložení nikdy přímo do zdrojového kódu.  Vložené klíče ze sestavení pomocí snadno přečíst [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je například Poznámkový blok.  
  
 Po dokončení pomocí kryptografického klíče, vymažte ho z paměti nastavením všech bajtů na hodnotu nula nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda třídy spravované kryptografie.  Kryptografické klíče můžete někdy se číst z paměti pomocí ladicího programu nebo z pevného disku Pokud stránkovaného umístění v paměti na disk.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>  
- [Postupy: Dešifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
