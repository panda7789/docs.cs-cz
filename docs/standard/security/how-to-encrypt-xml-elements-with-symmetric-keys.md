---
title: 'Postupy: Šifrování elementů XML pomocí symetrických klíčů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b792fd6eea0a33b0143fafa03641a78947d7e127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458068"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Postupy: Šifrování elementů XML pomocí symetrických klíčů
Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování elementu v dokumentu XML.  Šifrování XML umožňuje ukládat nebo přenášet citlivé XML, aniž byste se museli starat o data, která se dají snadno přečíst.  Tento postup šifruje XML element pomocí algoritmu standard AES (Advanced Encryption Standard) (AES), označovaného také jako Rijndael.  
  
 Informace o tom, jak dešifrovat XML element, který byl zašifrován pomocí tohoto postupu, naleznete v tématu [How to: deencrypt XML Elements with Symetrick Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 Pokud používáte symetrický algoritmus jako AES k šifrování dat XML, je nutné použít stejný klíč k šifrování a dešifrování dat XML.  V příkladu v tomto postupu se předpokládá, že zašifrovaný kód XML bude dešifrován pomocí stejného klíče a že zašifrované a dešifrovací strany souhlasí s algoritmem a klíčem, který se má použít.  Tento příklad neukládá nebo šifruje klíč AES v rámci šifrovaného kódu XML.  
  
 Tento příklad je vhodný pro situace, kdy jedna aplikace potřebuje šifrovat data na základě klíče relace uloženého v paměti nebo na základě kryptograficky silného klíče odvozeného od hesla.  V situacích, kdy je potřeba, aby dvě nebo více aplikací sdílely šifrovaná data XML, zvažte použití schématu šifrování založeného na asymetrickém algoritmu nebo certifikátu X. 509.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>Šifrování elementu XML pomocí symetrického klíče  
  
1. Vygenerujte symetrický klíč pomocí třídy <xref:System.Security.Cryptography.RijndaelManaged>.  Tento klíč se použije k zašifrování elementu XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. Vytvořte objekt <xref:System.Xml.XmlDocument> načtením souboru XML z disku.  Objekt <xref:System.Xml.XmlDocument> obsahuje element XML k zašifrování.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. Vyhledá zadaný element v objektu <xref:System.Xml.XmlDocument> a vytvoří nový objekt <xref:System.Xml.XmlElement>, který reprezentuje element, který chcete zašifrovat.  V tomto příkladu je prvek `"creditcard"` zašifrovaný.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. Vytvořte novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> a použijte ji k zašifrování <xref:System.Xml.XmlElement> symetrického klíče.  Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> vrátí zašifrovaný prvek jako pole šifrovaných bajtů.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. Sestavte objekt <xref:System.Security.Cryptography.Xml.EncryptedData> a naplňte ho identifikátorem URL XML elementu šifrování.  Tento identifikátor adresy URL umožňuje dešifrovací straně upozornit, že kód XML obsahuje zašifrovaný element.  K určení identifikátoru adresy URL můžete použít pole <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. Vytvořte objekt <xref:System.Security.Cryptography.Xml.EncryptionMethod>, který je inicializován na identifikátor adresy URL kryptografického algoritmu použitého k vygenerování klíče.  Předejte objekt <xref:System.Security.Cryptography.Xml.EncryptionMethod> do vlastnosti <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. Přidejte data šifrovaných prvků do objektu <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. Nahraďte prvek z původního objektu <xref:System.Xml.XmlDocument> prvkem <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a>Příklad  
  
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
  
- Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.  
  
- Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy neukládejte kryptografický klíč ve formátu prostého textu ani nepřenáší klíč mezi počítači ve formátu prostého textu.  Místo toho použijte k ukládání kryptografických klíčů zabezpečený kontejner klíčů.  
  
 Až budete s použitím kryptografického klíče hotovi, vymažte ho z paměti nastavením každého bajtu na nulu nebo voláním metody <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> spravované kryptografické třídy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Dešifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
