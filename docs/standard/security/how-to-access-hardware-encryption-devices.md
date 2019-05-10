---
title: 'Postupy: Přístup k hardwarovým šifrovacím zařízením'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c16c994e3976fb3ee569799461db1d1789a6186
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654384"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Postupy: Přístup k hardwarovým šifrovacím zařízením
Můžete použít <xref:System.Security.Cryptography.CspParameters> třídy pro přístup k hardwarovým šifrovacím zařízením. Tato třída můžete například použít k integraci vaší aplikace pomocí čipové karty, generátor náhodných čísel hardware nebo hardware provádění konkrétní kryptografický algoritmus.  
  
 <xref:System.Security.Cryptography.CspParameters> Třída vytvoří zprostředkovatele kryptografických služeb (CSP), který přistupuje k správně nainstalována hardwarové šifrování zařízení.  Dostupnost služby Zprostředkovatel kryptografických služeb můžete ověřit kontrolou následující klíč registru, pomocí Editoru registru (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Podepsat data pomocí klíčů karty  
  
1. Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy, prochází zprostředkovatele typu celé číslo a název poskytovatele pro konstruktor.  
  
2. Předat vhodné příznaky <xref:System.Security.Cryptography.CspParameters.Flags%2A> vlastnosti nově vytvořeného <xref:System.Security.Cryptography.CspParameters> objektu.  Například předání <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> příznak.  
  
3. Vytvořit novou instanci třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (například <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy), předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.  
  
4. Podepište data pomocí jedné z `Sign` metody a ověření pomocí jedné z dat `Verify` metody.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Generovat náhodné číslo pomocí hardwaru generátor náhodných čísel  
  
1. Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy, prochází zprostředkovatele typu celé číslo a název poskytovatele pro konstruktor.  
  
2. Vytvořit novou instanci třídy <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.  
  
3. Vytvořit náhodnou hodnotu pomocí <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> nebo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak podepsat data pomocí čipové karty.  Příklad kódu vytvoří <xref:System.Security.Cryptography.CspParameters> objekt, který zpřístupňuje čipových karet a poté inicializuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> pomocí CSP.  Příklad kódu a podepíše a ověří nějaká data.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Zahrnout <xref:System> a <xref:System.Security.Cryptography> obory názvů.  
  
- Musíte mít čtečku čipových karet a ovladače v počítači nainstalována.  
  
- Je třeba inicializovat <xref:System.Security.Cryptography.CspParameters> pomocí informací specifických pro vaši čtečku.  Další informace naleznete v dokumentaci vaši čtečku.
