---
title: "Postupy: Dešifrování elementů XML pomocí symetrických klíčů"
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
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ac84956e8b80dbc91fa59af3ae0f33d18112a9a2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Postupy: Dešifrování elementů XML pomocí symetrických klíčů
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> obor názvů pro zašifrování element dokumentu XML.  XML – šifrování umožňuje uložit nebo přenosu citlivých XML bez obav data snadno čitelná.  Tento příklad kódu dešifruje element XML pomocí algoritmus Advanced Encryption (Standard AES), také označován jako Rijndael.  
  
 Informace o tom, jak šifrování elementu XML s použitím tohoto postupu najdete v tématu [postupy: šifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Použijete-li k šifrování dat XML symetrický algoritmus jako je AES, musíte použít stejný klíč k šifrování a dešifrování dat XML.  Příklad v tomto postupu předpokládá, že šifrované XML byla zašifrována pomocí stejného klíče, a šifrování a dešifrování strany ke shodě o algoritmus a klíč k použití.  V tomto příkladu se neukládají ani šifrování AES klíč v šifrované kódu XML.  
  
 Tento příklad je vhodný pro situace, kdy jediná aplikace potřebuje k šifrování dat na základě relace klíče uložené v paměti, nebo podle kryptograficky silnou klíče odvozeného z hesla.  V situacích, kdy je potřeba sdílet šifrovaná data XML dvě nebo více aplikací zvažte použití schématu šifrování na základě asymetrického algoritmu nebo certifikát X.509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>K dešifrování symetrického klíče elementu XML  
  
1.  Zašifrování elementu XML vytvořených předtím klíčem pomocí technik popsaných v [postupy: šifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2.  Najít <`EncryptedData`> elementu (definované XML Encryption standard) v <xref:System.Xml.XmlDocument> objektu, který obsahuje XML zašifrované a vytvořte novou <xref:System.Xml.XmlElement> objekt představující tento element.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  Vytvoření <xref:System.Security.Cryptography.Xml.EncryptedData> objekt načtením nezpracovaná data XML z dříve vytvořeného <xref:System.Xml.XmlElement> objektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  Vytvořte novou <xref:System.Security.Cryptography.Xml.EncryptedXml> objektu a použít ho k dešifrování dat XML pomocí stejného klíče, která byla použita pro šifrování.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  Nahraďte element šifrované element nově dešifrovaným ve formátu prostého textu v dokumentu XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.  
  
-   Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy uložení kryptografického klíče v podobě prostého textu nebo přenos klíče mezi počítači v podobě prostého textu.  
  
 Po dokončení pomocí symetrický šifrovací klíč, zrušte ji z paměti nastavením všech bajtů na nulu nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda spravované kryptografické třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography.Xml>  
 [Postupy: Šifrování elementů XML pomocí symetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
