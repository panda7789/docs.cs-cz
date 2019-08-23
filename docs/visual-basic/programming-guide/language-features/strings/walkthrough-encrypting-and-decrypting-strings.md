---
title: Šifrování a dešifrování řetězců v Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: ee8691fedb537d1aa588eaac61624b445da64d1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944427"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Návod: Šifrování a dešifrování řetězců v Visual Basic
V <xref:System.Security.Cryptography.DESCryptoServiceProvider> tomto návodu se dozvíte, jak používat třídu pro šifrování a dešifrování řetězců pomocí verze zprostředkovatele kryptografických služeb (CSP) algoritmu Triple Data Encryption Standard<xref:System.Security.Cryptography.TripleDES>(). Prvním krokem je vytvořit jednoduchou obálkovou třídu, která zapouzdřuje algoritmus 3DES a uloží šifrovaná data jako řetězec s kódováním Base-64. Tato obálka pak slouží k bezpečnému ukládání privátních uživatelských dat do veřejně přístupného textového souboru.  
  
 Šifrování můžete použít k ochraně uživatelských tajných klíčů (například hesel) a k zpřístupnění přihlašovacích údajů neautorizovanými uživateli. To může chránit identitu oprávněného uživatele proti krádeži, která chrání prostředky uživatele a zajišťuje Neodmítnutí. Šifrování může také chránit data uživatele před přístupem neautorizovaných uživatelů.  
  
 Další informace najdete v tématu [kryptografické služby](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
> Rozhraní Rijndael (nyní označované jako standard AES (Advanced Encryption Standard) [AES]) a algoritmy 3DES (Triple Data Encryption Standard) poskytují lepší zabezpečení než algoritmus DES, protože jsou výpočty mnohem náročné. Další informace naleznete v tématu <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Vytvoření obálky pro šifrování  
  
1. `Simple3Des` Vytvořte třídu pro zapouzdření šifrovacích a dešifrovacích metod.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Přidejte import oboru názvů kryptografie na začátek souboru, který obsahuje `Simple3Des` třídu.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. `Simple3Des` Ve třídě přidejte soukromé pole pro uložení poskytovatele kryptografických služeb 3DES.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Přidejte soukromou metodu, která vytvoří pole bajtů o zadané délce z hodnoty hash zadaného klíče.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. Přidejte konstruktor pro inicializaci zprostředkovatele kryptografických služeb 3DES.  
  
     Parametr řídí metody`DecryptData` a `EncryptData`. `key`  
  
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
  
3. Přidejte kód uživatelského rozhraní pro volání `TestEncoding` metod a. `TestDecoding`  
  
4. Spusťte aplikaci.  
  
     Když otestujete aplikaci, Všimněte si, že nebude dešifrovat data, pokud zadáte chybné heslo.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
