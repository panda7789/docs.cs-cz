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
ms.openlocfilehash: 2ebf3f86ac550c0179b2e26879a7df128fd529e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706094"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Postupy: Šifrování elementů XML pomocí asymetrických klíčů
Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování elementu v dokumentu XML.  Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.  Další informace o standardu šifrování XML najdete v tématu Specifikace konsorcium World Wide Web (W3C) pro šifrování XML umístěné v <https://www.w3.org/TR/xmldsig-core/>.  
  
 Můžete použít šifrování XML k nahrazení libovolného elementu XML nebo dokumentu pomocí <`EncryptedData`> elementu, který obsahuje šifrovaná data XML.  Prvek <`EncryptedData`> může také obsahovat dílčí prvky, které obsahují informace o klíčích a procesech použitých při šifrování.  Šifrování XML umožňuje dokumentu obsahovat více šifrovaných prvků a umožňuje vícenásobné šifrování elementu.  Příklad kódu v tomto postupu ukazuje, jak vytvořit <`EncryptedData`> prvek spolu s několika dalšími dílčími prvky, které můžete použít později během dešifrování.  
  
 Tento příklad šifruje XML element pomocí dvou klíčů.  Vygeneruje pár veřejného a privátního klíče RSA a uloží dvojici klíčů do zabezpečeného kontejneru klíčů.  Příklad následně vytvoří samostatný klíč relace pomocí algoritmu standard AES (Advanced Encryption Standard) (AES), který se označuje také jako algoritmus Rijndael.  V příkladu je použit klíč relace AES k šifrování dokumentu XML a poté používá veřejný klíč RSA k šifrování klíče relace AES.  Nakonec příklad uloží šifrovaný klíč relace AES a zašifrovaná data XML do dokumentu XML v rámci nového <`EncryptedData`> elementu.  
  
 Chcete-li dešifrovat XML element, načtěte privátní klíč RSA z kontejneru klíčů, použijte ho k dešifrování klíče relace a pak použijte klíč relace k dešifrování dokumentu.  Další informace o tom, jak dešifrovat XML element, který byl zašifrovaný pomocí tohoto postupu, naleznete v tématu [How to: deencrypt XML Elements with asymetrické klíče](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Tento příklad je vhodný pro situace, kdy více aplikací potřebuje sdílet šifrovaná data nebo kde aplikace potřebuje ukládat šifrovaná data mezi časy, ve kterých běží.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Šifrování elementu XML pomocí asymetrického klíče  
  
1. Vytvořte objekt <xref:System.Security.Cryptography.CspParameters> a zadejte název kontejneru klíčů.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Vygenerujte symetrický klíč pomocí třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Klíč se automaticky uloží do kontejneru klíčů při předání objektu <xref:System.Security.Cryptography.CspParameters> do konstruktoru třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Tento klíč se použije k zašifrování klíče relace AES a bude možné ho později načíst k dešifrování.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.  Objekt <xref:System.Xml.XmlDocument> obsahuje element XML k zašifrování.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. Vyhledá zadaný element v objektu <xref:System.Xml.XmlDocument> a vytvoří nový objekt <xref:System.Xml.XmlElement>, který reprezentuje element, který chcete zašifrovat. V tomto příkladu je prvek `"creditcard"` zašifrovaný.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. Vytvořte nový klíč relace pomocí třídy <xref:System.Security.Cryptography.RijndaelManaged>.  Tento klíč zašifruje XML element a pak bude zašifrovaný a umístěný v dokumentu XML.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. Vytvořte novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> a použijte ji k zašifrování zadaného elementu pomocí klíče relace.  Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> vrátí zašifrovaný prvek jako pole šifrovaných bajtů.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. Sestavte objekt <xref:System.Security.Cryptography.Xml.EncryptedData> a naplňte ho identifikátorem URL šifrovaného elementu XML.  Tento identifikátor adresy URL umožňuje dešifrovací straně upozornit, že kód XML obsahuje zašifrovaný element.  K určení identifikátoru adresy URL můžete použít pole <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>.  Nešifrovaný element XML bude nahrazen <`EncryptedData`> element zapouzdřený tímto <xref:System.Security.Cryptography.Xml.EncryptedData>m objektem.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. Vytvořte objekt <xref:System.Security.Cryptography.Xml.EncryptionMethod>, který je inicializován na identifikátor adresy URL kryptografického algoritmu používaného k vygenerování klíče relace.  Předejte objekt <xref:System.Security.Cryptography.Xml.EncryptionMethod> do vlastnosti <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Vytvořte objekt <xref:System.Security.Cryptography.Xml.EncryptedKey>, který bude obsahovat zašifrovaný klíč relace.  Zašifrujte klíč relace, přidejte ho do objektu <xref:System.Security.Cryptography.Xml.EncryptedKey> a zadejte název klíče relace a adresu URL identifikátoru klíče.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Vytvoří nový objekt <xref:System.Security.Cryptography.Xml.DataReference>, který mapuje šifrovaná data na konkrétní klíč relace.  Tento volitelný krok umožňuje snadno určit, že více částí dokumentu XML bylo zašifrováno jedním klíčem.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Přidejte šifrovaný klíč do objektu <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Vytvořte nový objekt <xref:System.Security.Cryptography.Xml.KeyInfo> pro zadání názvu klíče RSA.  Přidejte jej do objektu <xref:System.Security.Cryptography.Xml.EncryptedData>. To pomáhá dešifrovací straně identifikovat správný asymetrický klíč, který se má použít při dešifrování klíče relace.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Přidejte data šifrovaných prvků do objektu <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Nahraďte prvek z původního objektu <xref:System.Xml.XmlDocument> prvkem <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Uložte objekt <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.  
  
- Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy neukládejte symetrický kryptografický klíč ve formě prostého textu nebo přenášet symetrický klíč mezi počítači ve formátu prostého textu.  Kromě toho nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.  Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy nevkládat klíč přímo do zdrojového kódu.  Vložené klíče lze snadno přečíst ze sestavení pomocí nástroje [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.  
  
 Až budete s použitím kryptografického klíče hotovi, vymažte ho z paměti nastavením každého bajtu na nulu nebo voláním metody <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> spravované kryptografické třídy.  Kryptografické klíče je někdy možné z paměti načítat pomocí ladicího programu nebo je číst z pevného disku, pokud je umístění v paměti stránkované na disk.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Dešifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
