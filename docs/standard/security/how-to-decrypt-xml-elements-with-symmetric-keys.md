---
title: 'Postupy: Dešifrování elementů XML pomocí symetrických klíčů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: bb34332d345ee7bcb9037dc7bdf0deebbe70c3c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277424"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Postupy: Dešifrování elementů XML pomocí symetrických klíčů
Třídy v <xref:System.Security.Cryptography.Xml> oboru názvů můžete použít k zašifrování elementu v dokumentu XML.  Šifrování XML umožňuje ukládat nebo přenášet citlivé XML, aniž byste se museli starat o data, která se dají snadno přečíst.  Tento příklad kódu dešifruje XML element pomocí algoritmu standard AES (Advanced Encryption Standard) (AES), označovaného také jako Rijndael.  
  
 Informace o tom, jak zašifrovat XML element pomocí tohoto postupu, naleznete v tématu [How to: ENCRYPT XML Elements with Symetrick Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Pokud používáte symetrický algoritmus jako AES k šifrování dat XML, je nutné použít stejný klíč k šifrování a dešifrování dat XML.  V příkladu v tomto postupu se předpokládá, že zašifrovaný kód XML byl zašifrovaný pomocí stejného klíče a že zašifrované a dešifrovací strany souhlasí s algoritmem a klíčem, který se má použít.  Tento příklad neukládá nebo šifruje klíč AES v rámci šifrovaného kódu XML.  
  
 Tento příklad je vhodný pro situace, kdy jedna aplikace potřebuje šifrovat data na základě klíče relace uloženého v paměti nebo na základě kryptograficky silného klíče odvozeného od hesla.  V situacích, kdy je potřeba, aby dvě nebo více aplikací sdílely šifrovaná data XML, zvažte použití schématu šifrování založeného na asymetrickém algoritmu nebo certifikátu X. 509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>Dešifrování elementu XML symetrickým klíčem  
  
1. Šifrujte XML element pomocí dříve vygenerovaného klíče pomocí technik popsaných v tématu [Postupy: šifrování elementů XML pomocí symetrických klíčů](how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2. Vyhledejte prvek <`EncryptedData`> (definovaný standardem šifrování XML) v <xref:System.Xml.XmlDocument> objektu, který obsahuje šifrovaný kód XML a vytvořte nový <xref:System.Xml.XmlElement> objekt pro reprezentaci tohoto prvku.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. Vytvořte <xref:System.Security.Cryptography.Xml.EncryptedData> objekt načtením nezpracovaných dat XML z dříve vytvořeného <xref:System.Xml.XmlElement> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. Vytvořte nový <xref:System.Security.Cryptography.Xml.EncryptedXml> objekt a použijte ho k dešifrování dat XML pomocí stejného klíče, který se použil pro šifrování.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. Nahraďte zašifrovaný element nově dešifrovaným nešifrovaným elementem v dokumentu XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Chcete-li tento příklad zkompilovat, je nutné zahrnout odkaz na `System.Security.dll` .  
  
- Zahrňte následující obory názvů: <xref:System.Xml> , <xref:System.Security.Cryptography> a <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy neukládejte kryptografický klíč ve formátu prostého textu ani nepřenáší klíč mezi počítači ve formátu prostého textu.  
  
 Po dokončení používání symetrického kryptografického klíče jej vymažte z paměti nastavením každého bajtu na hodnotu nula nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody spravované kryptografické třídy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Šifrování elementů XML pomocí symetrických klíčů](how-to-encrypt-xml-elements-with-symmetric-keys.md)
