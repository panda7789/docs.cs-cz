---
title: Šifrování a dešifrování řetězců v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 1d003df87327e14a6cbd65222f86c3dc4df169ff
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334039"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Návod: Šifrování a dešifrování řetězců v jazyce Visual Basic
Tento návod ukazuje, jak používat <xref:System.Security.Cryptography.DESCryptoServiceProvider> třídy k šifrování a dešifrování řetězců v kódu pomocí verze zprostředkovatele kryptografických služeb Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algoritmus. Prvním krokem je vytvoření jednoduchého obálkovou třídu, která zapouzdřuje algoritmus 3DES a šifrovaná data uloží jako kódovaný řetězec base-64. Potom tuto obálku slouží k bezpečné ukládání privátních dat uživatele ve veřejně přístupné textového souboru.  
  
 Šifrování můžete použít k ochraně tajných kódů uživatelů (například hesla) a aby přihlašovací údaje nejde přečíst neoprávnění uživatelé. To může chránit identity autorizovaný uživatel z jeho krádeže, které chrání prostředky uživatele a poskytuje nepopiratelnosti. Šifrování může také chránit data uživatele přístup neoprávnění uživatelé.  
  
 Další informace najdete v tématu [šifrovacím službám](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  Rijndael (dnes označovány jako na 256bitovém standardu [AES]) a algoritmus Triple Data Encryption Standard (3DES) poskytuje lepší zabezpečení než DES vzhledem k tomu, že jsou další výpočetně náročné. Další informace naleznete v tématu <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Chcete-li vytvořit obálky šifrování  
  
1. Vytvořte `Simple3Des` třídy k zapouzdření metody šifrování a dešifrování.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Přidejte na začátek souboru, který obsahuje import oboru názvů kryptografie `Simple3Des` třídy.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. V `Simple3Des` třídy, přidejte soukromé pole k ukládání zprostředkovatele kryptografických služeb 3DES.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Přidejte privátní metodu, která vytvoří bajtové pole zadané délky z hodnoty hash se zadaným klíčem.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. Přidejte konstruktor k inicializaci zprostředkovatele kryptografických služeb 3DES.  
  
     `key` Ovládací prvky parametrů `EncryptData` a `DecryptData` metody.  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Přidejte veřejnou metodu, která šifruje řetězce.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Přidejte veřejnou metodu, která dešifruje řetězec.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     Obálková třída nyní umožňuje chránit prostředky uživatele. V tomto příkladu se používá pro bezpečné ukládání privátních dat uživatele ve veřejně přístupné textového souboru.  
  
### <a name="to-test-the-encryption-wrapper"></a>K otestování obálky šifrování  
  
1. V samostatné třídě, přidejte metodu, která používá obálku pro `EncryptData` metodu zašifrovat řetězec a zapsat pro uživatele vaší složky Dokumenty.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Přidejte metodu, která čte zašifrovaný řetězec od uživatele je složka Dokumenty a dešifruje řetězce bez prvku obálky `DecryptData` metody.  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. Přidejte kód uživatelského rozhraní pro volání `TestEncoding` a `TestDecoding` metody.  
  
4. Spusťte aplikaci.  
  
     Při testování aplikace, Všimněte si, že data se nebudou dešifrovat, pokud zadáte nesprávné heslo.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Šifrovací služby](../../../../standard/security/cryptographic-services.md)
