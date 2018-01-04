---
title: "Postupy: Dešifrování elementů XML pomocí asymetrických klíčů"
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
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 099937fe113c39c717b4c9fcba2042115b9105e6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Postupy: Dešifrování elementů XML pomocí asymetrických klíčů
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování a dešifrování element dokumentu XML.  XML – šifrování je standardní způsob, jak exchange nebo uložit šifrovaná data XML, bez starostí o data snadno čitelná.  Další informace o standardu XML – šifrování najdete v tématu doporučení World Wide Web Consortium (W3C) [syntaxe podpis XML a zpracování](http://go.microsoft.com/fwlink/?LinkID=136777).  
  
 V příkladu v tomto postupu dešifruje element XML, který byl zašifrován pomocí metody popsané v [postupy: šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Najde <`EncryptedData`> elementu, element dešifruje a element nahradí původní element XML ve formátu prostého textu.  
  
 Tento příklad dešifruje element XML pomocí dva klíče.  Načte dříve vytvořený privátní klíč RSA z kontejneru klíčů, a pak používá klíč RSA k dešifrování klíče relace uloženy v <`EncryptedKey`> elementu <`EncryptedData`> elementu.  V příkladu pak používá klíč relace k dešifrování elementu XML.  
  
 Tento příklad je vhodný pro situace, kdy se více aplikací mít sdílet šifrovaná data nebo které má aplikace uložit šifrovaná data v době mezi spuštěné.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Dešifrování elementu XML asymetrickým klíčem  
  
1.  Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Načíst dříve vygenerovaný asymetrický klíč z kontejneru pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu.  Klíč je automaticky načte z kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> do objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> konstruktor.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Vytvořte novou <xref:System.Security.Cryptography.Xml.EncryptedXml> objektu k dešifrování dokumentu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  Přidáte mapování název klíče nebo klíče RSA přidružit elementu v dokumentu, který by měl být dešifrován.  Musíte použít stejný název pro klíč, který jste použili při šifrování dokumentu.  Všimněte si, že tento název je oddělený od název sloužící k identifikaci klíče v kontejneru klíčů v kroku 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  Volání <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda dešifrovat <`EncryptedData`> elementu.  Tato metoda používá klíč RSA k dešifrování klíče relace a automaticky používá klíč relace k dešifrování elementu XML.  Také automaticky nahradí <`EncryptedData`> element s původní ve formátu prostého textu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  Uložte dokument XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Příklad  
 Tento příklad předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako zkompilovaný program.  Dále předpokládá, že `test.xml` obsahuje element XML, který byl zašifrován pomocí technik popsaných v [postupy: šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Pro zkompilování tohoto příkladu, budete muset obsahovat odkaz na `System.Security.dll`.  
  
-   Zahrnout následujících oborů názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy neukládají symetrický kryptografický klíč ve formátu prostého textu nebo přeneste symetrického klíče mezi počítači v podobě prostého textu.  Kromě toho nikdy uložení nebo přeneste privátní klíč pár asymetrických klíčů ve formátu prostého textu.  Další informace o symetrické a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy nevkládejte klíč přímo do zdrojového kódu.  Vložené klíče můžete snadno přečíst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, například Poznámkový blok.  
  
 Po dokončení pomocí kryptografického klíče, vymazat z paměti nastavením všech bajtů na nulu nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda spravované kryptografické třídy.  Kryptografické klíče v některých případech můžete číst z paměti ladicí program nebo číst z pevného disku, pokud je stránkovaného umístění v paměti na disk.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography.Xml>  
 [Postupy: Šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
