---
title: Šifrování a dešifrování řetězců v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 96e56ab315a739fef9d5499b076a077f5294f39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651220"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Návod: Šifrování a dešifrování řetězců v jazyce Visual Basic
Tento postup vám ukáže, jak používat <xref:System.Security.Cryptography.DESCryptoServiceProvider> třída k šifrování a dešifrování řetězců pomocí kryptografických služeb verze zprostředkovatele Kryptografických služeb Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algoritmus. Prvním krokem je vytvoření jednoduché obálkovou třídu, který zapouzdřuje algoritmus 3DES a šifrovaná data uloží jako řetězec s kódováním base-64. Potom tuto obálku slouží bezpečně uložit privátních dat uživatele do veřejně přístupné textového souboru.  
  
 Šifrování můžete použít k ochraně tajných klíčů uživatele (například hesla) a tak, aby pověření nečitelná neoprávnění uživatelé. To může chránit oprávněný uživatel identity z krádeže, které chrání prostředky uživatele a poskytuje zrušení odmítnutí. Šifrování může také chránit data uživatele z Probíhá přístup neoprávnění uživatelé.  
  
 Další informace najdete v tématu [šifrovacím službám](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  Rijndael (nyní označuje jako Advanced Encryption Standard [AES]) a Triple Data Encryption Standard (3DES) algoritmy poskytují vyšší zabezpečení než šifrování DES, protože jsou další výpočetně náročné. Další informace naleznete v tématu <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Chcete-li vytvořit obálku šifrování  
  
1.  Vytvořte `Simple3Des` Třída zapouzdření metody šifrování a dešifrování.  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Přidejte na začátek souboru, který obsahuje importu kryptografie oboru názvů `Simple3Des` třídy.  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  V `Simple3Des` třídy, přidejte soukromé pole k uložení zprostředkovatele kryptografických služeb 3DES.  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Přidejte soukromá metoda, která vytvoří bajtové pole o zadané délce z hodnota hash se zadaným klíčem.  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  Přidejte konstruktor k inicializaci zprostředkovatele kryptografických služeb 3DES.  
  
     `key` Ovládací prvky parametrů `EncryptData` a `DecryptData` metody.  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Přidejte veřejnou metodu, která zašifruje řetězec.  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Přidejte veřejnou metodu, která dešifruje řetězec.  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     Obálková třída teď umožňuje chránit prostředky uživatele. V tomto příkladu se používá bezpečně uložit privátních dat uživatele do veřejně přístupné textového souboru.  
  
### <a name="to-test-the-encryption-wrapper"></a>K testování obálku šifrování  
  
1.  V samostatné třídy, přidejte metodu, která používá obálku `EncryptData` metoda šifrování řetězec a zapsat pro uživatele je složka Dokumenty.  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Přidejte metodu, která čte zašifrovaný řetězec od uživatele je složka Dokumenty a dešifruje řetězec s Obálka `DecryptData` metoda.  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Přidejte kód uživatelského rozhraní k volání `TestEncoding` a `TestDecoding` metody.  
  
4.  Spusťte aplikaci.  
  
     Při testování aplikace, Všimněte si data ho nebude dešifrovat, pokud jste zadali nesprávné heslo.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
