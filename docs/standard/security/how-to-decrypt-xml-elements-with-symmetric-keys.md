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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c569407bac247e60075834e67fde9327ce6bc4a0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334624"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Postupy: Dešifrování elementů XML pomocí symetrických klíčů
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování element v dokumentu XML.  Šifrování XML můžete uložit nebo přenosu citlivých XML, nemusíme mít starosti se snadno číst data.  Tento příklad kódu dešifruje elementu XML použitím algoritmus Advanced Encryption (Standard AES), také označován jako Rijndael.  
  
 Informace o tom, jak šifrování XML elementu s použitím tohoto postupu najdete v tématu [jak: Šifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Při použití symetrický algoritmus, jako je AES pro šifrování dat XML, musí používat stejný klíč k šifrování a dešifrování dat XML.  V příkladu v tomto postupu se předpokládá, že šifrované XML byla zašifrována pomocí stejného klíče, a šifrování a dešifrování strany shodnout na algoritmus a klíč.  V tomto příkladu se neukládají ani šifrování AES klíč v souboru XML zašifrované.  
  
 Tento příklad je vhodný pro situace, kdy jedné aplikace potřebuje k šifrování dat na základě relace klíče uložené v paměti, nebo podle přidělení kryptograficky silného klíče odvozeného z hesla.  V situacích, kdy je potřeba sdílet šifrovaná data XML dva nebo více aplikací zvažte použití schématu šifrování na základě asymetrického algoritmu nebo certifikát X.509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>K dešifrování symetrického klíče elementu XML  
  
1. Šifrování XML element s dříve vytvořenou klíče pomocí technik popsaných v [jak: Šifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2. Najít <`EncryptedData`> – element (definované XML Encryption standard) v <xref:System.Xml.XmlDocument> objekt, který obsahuje zašifrované XML a vytvořte nový <xref:System.Xml.XmlElement> objekt představující tento prvek.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedData> objekt načtením nezpracovaná data XML z dříve vytvořeného <xref:System.Xml.XmlElement> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. Vytvořte nový <xref:System.Security.Cryptography.Xml.EncryptedXml> objektu a použít ho k dešifrování dat XML pomocí stejného klíče, který se používá pro šifrování.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. Šifrovaný element nahraďte element nově dešifrovaný ve formátu prostého textu v dokumentu XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.  
  
-   Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy uložení kryptografického klíče ve formátu prostého textu nebo přenosu klíče mezi počítači ve formátu prostého textu.  
  
 Po dokončení pomocí symetrické kryptografické klíče, vymažte ho z paměti nastavením všech bajtů na hodnotu nula nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda třídy spravované kryptografie.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Šifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
