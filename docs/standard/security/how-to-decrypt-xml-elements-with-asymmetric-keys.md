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
ms.openlocfilehash: 5ed1e2eb2518366da0a57655d7a8691e23f725d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706133"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Postupy: Dešifrování elementů XML pomocí asymetrických klíčů
Můžete použít třídy v oboru názvů <xref:System.Security.Cryptography.Xml> k zašifrování a dešifrování elementu v dokumentu XML.  Šifrování XML je standardní způsob, jak vyměňovat nebo ukládat šifrovaná data XML, aniž byste se museli snadno přečíst.  Další informace o standardu šifrování XML najdete v tématu [syntaxe a zpracování signatur XML](https://www.w3.org/TR/xmldsig-core/)doporučení pro konsorcium World Wide Web (W3C).  
  
 Příklad v tomto postupu dešifruje XML element, který byl zašifrován pomocí metod popsaných v tématu [Postupy: šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Najde <`EncryptedData`> element, dešifruje prvek a pak nahradí element původním nešifrovaným XML elementem.  
  
 Tento příklad dešifruje XML element pomocí dvou klíčů.  Načte dříve vygenerovaný privátní klíč RSA z kontejneru klíčů a potom pomocí klíče RSA dešifruje klíč relace uložený ve <`EncryptedKey`> elementu <`EncryptedData`> elementu.  Příklad poté používá klíč relace k dešifrování XML elementu.  
  
 Tento příklad je vhodný pro situace, kdy více aplikací musí sdílet šifrovaná data nebo kde aplikace musí ukládat šifrovaná data mezi časy, ve kterých je spuštěná.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Dešifrování elementu XML pomocí asymetrického klíče  
  
1. Vytvořte objekt <xref:System.Security.Cryptography.CspParameters> a zadejte název kontejneru klíčů.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Načte dříve generovaný asymetrický klíč z kontejneru pomocí objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Klíč je automaticky načten z kontejneru klíčů při předání objektu <xref:System.Security.Cryptography.CspParameters> do konstruktoru <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Vytvořte nový objekt <xref:System.Security.Cryptography.Xml.EncryptedXml> k dešifrování dokumentu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. Přidejte mapování klíč/název pro přidružení klíče RSA k elementu v dokumentu, který má být dešifrován.  Pro klíč, který jste použili při šifrování dokumentu, je nutné použít stejný název.  Všimněte si, že tento název je oddělený od názvu používaného k identifikaci klíče v kontejneru klíčů zadaného v kroku 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. Zavolejte metodu <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> pro dešifrování <`EncryptedData`elementu >.  Tato metoda používá klíč RSA k dešifrování klíče relace a automaticky používá klíč relace k dešifrování XML elementu.  Také automaticky nahradí <`EncryptedData`> prvek původním prostým textem.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. Uložte dokument XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se předpokládá, že soubor s názvem `test.xml` existuje ve stejném adresáři jako kompilovaný program.  Předpokládá také, že `test.xml` obsahuje XML element, který byl zašifrován pomocí metod popsaných v tématu [How to: ENCRYPT XML Elements with asymetrické klíče](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Chcete-li tento příklad zkompilovat, je třeba zahrnout odkaz na `System.Security.dll`.  
  
- Zahrňte následující obory názvů: <xref:System.Xml>, <xref:System.Security.Cryptography>a <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nikdy neukládejte symetrický kryptografický klíč ve formě prostého textu nebo přenášet symetrický klíč mezi počítači ve formátu prostého textu.  Kromě toho nikdy Neukládat ani nepřenášet privátní klíč dvojice asymetrických klíčů ve formátu prostého textu.  Další informace o symetrických a asymetrických kryptografických klíčích najdete v tématu [generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nikdy nevkládat klíč přímo do zdrojového kódu.  Vložené klíče lze snadno přečíst ze sestavení pomocí [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo otevřením sestavení v textovém editoru, jako je Poznámkový blok.  
  
 Až budete s použitím kryptografického klíče hotovi, vymažte ho z paměti nastavením každého bajtu na nulu nebo voláním metody <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> spravované kryptografické třídy.  Kryptografické klíče je někdy možné z paměti načítat pomocí ladicího programu nebo je číst z pevného disku, pokud je umístění v paměti stránkované na disk.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.Xml>
- [Postupy: Šifrování elementů XML pomocí asymetrických klíčů](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
