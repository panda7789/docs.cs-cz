---
title: 'Postupy: Dešifrování elementů XML pomocí asymetrických klíčů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 303c7db984b682d24a8f0e00160eb2d0827a84e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314422"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Postupy: Dešifrování elementů XML pomocí asymetrických klíčů
Můžete použít třídy v <xref:System.Security.Cryptography.Xml> oboru názvů k šifrování a dešifrování element v dokumentu XML.  Šifrování XML je standardní způsob pro výměnu nebo ukládání zašifrovaných dat XML, nemusíme mít starosti se snadno číst data.  Další informace o standardních šifrování XML, naleznete v tématu World Wide Web Consortium (W3C) doporučení [podpis syntaxe jazyka XML a zpracování](https://www.w3.org/TR/xmldsig-core/).  
  
 V příkladu v tomto postupu dešifruje elementu XML, který byl zašifrován pomocí metod popsaných v [jak: Šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Najde <`EncryptedData`> element, dešifruje element a element nahradí původní element XML ve formátu prostého textu.  
  
 V tomto příkladu dešifruje elementu XML s použitím dva klíče.  Obnoví dříve vygenerovaný soukromý klíč RSA z kontejneru klíčů, a pak používá klíč RSA k dešifrování klíče relace uloženy v <`EncryptedKey`> element <`EncryptedData`> element.  Příklad poté používá klíč relace k dešifrování XML element.  
  
 Tento příklad je vhodný pro situace, kdy se více aplikací mají sdílet šifrovaná data nebo pokud aplikace musí uložit šifrovaná data mezi časem, které poběží.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>K dešifrování platný element XML s asymetrický klíč  
  
1. Vytvoření <xref:System.Security.Cryptography.CspParameters> objektu a zadejte název kontejneru klíčů.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Načíst dříve vytvořenou asymetrického klíče z kontejneru použijte <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu.  Klíč je automaticky načte z kontejneru klíčů při předání <xref:System.Security.Cryptography.CspParameters> objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> konstruktoru.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Vytvořte nový <xref:System.Security.Cryptography.Xml.EncryptedXml> objektu k dešifrování dokumentu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. Přidáte mapování klíč nebo název přidružení klíče RSA k prvku v rámci dokumentu, který by měl být dešifrován.  Je nutné použít stejný název klíče, který jste použili při šifrování dokumentu.  Všimněte si, že tento název je oddělené od název používaný k identifikaci klíče v kontejneru klíčů určeném v kroku 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. Volání <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metoda k dešifrování <`EncryptedData`> element.  Tato metoda používá klíč RSA k dešifrování klíče relace a automaticky použije klíč relace k dešifrování XML element.  Také automaticky nahradí <`EncryptedData`> element s původní ve formátu prostého textu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. Uložte dokument XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Příklad  
 Tento příklad předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako zkompilovaný program.  Dále předpokládá, že `test.xml` obsahuje element XML, který byl zašifrován pomocí technik popsaných v [jak: Šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Chcete-li kompilaci tohoto příkladu, je potřeba zahrnout odkaz na `System.Security.dll`.  
  
-   Následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>, a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy ukládat symetrický šifrovací klíč ve formátu prostého textu nebo přenášet symetrického klíče mezi počítači ve formátu prostého textu.  Kromě toho nikdy ukládat nebo přenášet privátní klíč pro pár asymetrických klíčů ve formátu prostého textu.  Další informace o symetrický a asymetrické kryptografické klíče najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Klíč pro vložení nikdy přímo do zdrojového kódu.  Vložené klíče můžete snadno číst ze sestavení pomocí [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je například Poznámkový blok.  
  
 Po dokončení pomocí kryptografického klíče, vymažte ho z paměti nastavením všech bajtů na hodnotu nula nebo voláním <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metoda třídy spravované kryptografie.  Kryptografické klíče můžete někdy se číst z paměti pomocí ladicího programu nebo z pevného disku Pokud stránkovaného umístění v paměti na disk.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
