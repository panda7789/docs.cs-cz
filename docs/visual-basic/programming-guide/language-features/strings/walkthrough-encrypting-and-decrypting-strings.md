---
title: Šifrování a dešifrování řetězců
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 36e405c7362993471d3e6da8e319bccb854e1026
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343587"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Návod: Šifrování a dešifrování řetězců v jazyce Visual Basic
V tomto návodu se dozvíte, jak používat třídu <xref:System.Security.Cryptography.DESCryptoServiceProvider> k šifrování a dešifrování řetězců pomocí verze zprostředkovatele kryptografických služeb (CSP) algoritmu Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>). Prvním krokem je vytvořit jednoduchou obálkovou třídu, která zapouzdřuje algoritmus 3DES a uloží šifrovaná data jako řetězec s kódováním Base-64. Tato obálka pak slouží k bezpečnému ukládání privátních uživatelských dat do veřejně přístupného textového souboru.  
  
 Šifrování můžete použít k ochraně uživatelských tajných klíčů (například hesel) a k zpřístupnění přihlašovacích údajů neautorizovanými uživateli. To může chránit identitu oprávněného uživatele proti krádeži, která chrání prostředky uživatele a zajišťuje Neodmítnutí. Šifrování může také chránit data uživatele před přístupem neautorizovaných uživatelů.  
  
 Další informace najdete v tématu [kryptografické služby](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
> Rozhraní Rijndael (nyní označované jako standard AES (Advanced Encryption Standard) [AES]) a algoritmy 3DES (Triple Data Encryption Standard) poskytují lepší zabezpečení než algoritmus DES, protože jsou výpočty mnohem náročné. Další informace naleznete v tématu <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Vytvoření obálky pro šifrování  
  
1. Vytvořte třídu `Simple3Des` pro zapouzdření šifrovacích a dešifrovacích metod.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Přidejte import oboru názvů kryptografie na začátek souboru, který obsahuje třídu `Simple3Des`.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. Ve třídě `Simple3Des` přidejte soukromé pole pro uložení poskytovatele kryptografických služeb 3DES.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Přidejte soukromou metodu, která vytvoří pole bajtů o zadané délce z hodnoty hash zadaného klíče.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. Přidejte konstruktor pro inicializaci zprostředkovatele kryptografických služeb 3DES.  
  
     Parametr `key` řídí metody `EncryptData` a `DecryptData`.  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Přidejte veřejnou metodu, která šifruje řetězec.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Přidejte veřejnou metodu, která dešifruje řetězec.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     Obálková třída se teď dá použít k ochraně prostředků uživatele. V tomto příkladu se používá k bezpečnému ukládání privátních uživatelských dat do veřejně přístupného textového souboru.  
  
### <a name="to-test-the-encryption-wrapper"></a>Otestování obálky šifrování  
  
1. V samostatné třídě přidejte metodu, která používá `EncryptData` metodu obálky k zašifrování řetězce a zapište ho do složky Dokumenty uživatele.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Přidejte metodu, která přečte zašifrovaný řetězec ze složky dokumenty daného uživatele a dešifruje řetězec pomocí `DecryptData` metody obálky.  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. Přidejte kód uživatelského rozhraní pro volání metod `TestEncoding` a `TestDecoding`.  
  
4. Spusťte aplikaci.  
  
     Když otestujete aplikaci, Všimněte si, že nebude dešifrovat data, pokud zadáte chybné heslo.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
