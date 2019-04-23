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
ms.openlocfilehash: 2268dc813d6f12b69bee99dd07f8f4431b12a283
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295624"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Postupy: Šifrování elementů XML pomocí symetrických klíčů
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování element v dokumentu XML.  Šifrování XML můžete uložit nebo přenosu citlivých XML, nemusíme mít starosti se snadno číst data.  Tento postup dešifruje elementu XML použitím algoritmus Advanced Encryption (Standard AES), také označován jako Rijndael.  
  
 Informace o tom, jak dešifrování elementu XML, který byl zašifrován pomocí tohoto postupu najdete v tématu [jak: Dešifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 Při použití symetrický algoritmus, jako je AES pro šifrování dat XML, musí používat stejný klíč k šifrování a dešifrování dat XML.  V příkladu v tomto postupu předpokládá, že budou šifrované XML dešifrována pomocí stejného klíče a, že šifrování a dešifrování strany shodnout na algoritmus a klíč.  V tomto příkladu se neukládají ani šifrování AES klíč v souboru XML zašifrované.  
  
 Tento příklad je vhodný pro situace, kdy jedné aplikace potřebuje k šifrování dat na základě relace klíče uložené v paměti, nebo podle přidělení kryptograficky silného klíče odvozeného z hesla.  V situacích, kdy je potřeba sdílet šifrovaná data XML dva nebo více aplikací zvažte použití schématu šifrování na základě asymetrického algoritmu nebo certifikát X.509.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>K šifrování se symetrickým klíčem XML element  
  
1. Vygenerovat symetrický klíč pomocí <xref:System.Security.Cryptography.RijndaelManaged> třídy.  Tento klíč se použije k zašifrování XML element.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. Vytvoření <xref:System.Xml.XmlDocument> objekt načtením souboru XML z disku.  <xref:System.Xml.XmlDocument> Objekt obsahuje element XML k šifrování.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. Najít zadaný element v <xref:System.Xml.XmlDocument> objektu a vytvořte nový <xref:System.Xml.XmlElement> objekt reprezentující element, který chcete zašifrovat.  V tomto příkladu `"creditcard"` šifrovaná prvku.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. Vytvořit novou instanci třídy <xref:System.Security.Cryptography.Xml.EncryptedXml> třídy a jeho pomocí šifrovat <xref:System.Xml.XmlElement> pomocí symetrického klíče.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda vrátí šifrovaný element jako pole šifrovaných bajtů.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedData> objektu a jeho naplnění identifikátor URL elementu šifrování XML.  Tento identifikátor URL umožňuje dešifrování strana vědět, že kód XML obsahuje šifrovaný element.  Můžete použít <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pole k určení identifikátoru adresy URL.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. Vytvoření <xref:System.Security.Cryptography.Xml.EncryptionMethod> , který je inicializován na identifikátor URL kryptografický algoritmus používaný k vygenerování klíče.  Předání <xref:System.Security.Cryptography.Xml.EncryptionMethod> objektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> vlastnost.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. Přidat data šifrovaný element <xref:System.Security.Cryptography.Xml.EncryptedData> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. Nahraďte element z původní <xref:System.Xml.XmlDocument> objektu <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
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
  
-   Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.  
  
-   Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy uložení kryptografického klíče ve formátu prostého textu nebo přenosu klíče mezi počítači ve formátu prostého textu.  Místo toho použijte zabezpečené kontejneru klíčů pro ukládání kryptografických klíčů.  
  
 Po dokončení pomocí kryptografického klíče, vymažte ho z paměti nastavením všech bajtů na hodnotu nula nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda třídy spravované kryptografie.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Dešifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
