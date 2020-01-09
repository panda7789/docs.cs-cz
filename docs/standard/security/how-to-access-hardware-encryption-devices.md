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
ms.openlocfilehash: d6ee22fd9fb0c11e22ac01ff83b3269e37e37763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706172"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Postupy: Přístup k hardwarovým šifrovacím zařízením
Pro přístup k hardwarovým šifrovacím zařízením můžete použít třídu <xref:System.Security.Cryptography.CspParameters>. Tuto třídu můžete například použít k integraci aplikace s čipovou kartou, generátor náhodných čísel hardwaru nebo implementaci hardwaru konkrétního šifrovacího algoritmu.  
  
 Třída <xref:System.Security.Cryptography.CspParameters> vytvoří zprostředkovatele kryptografických služeb (CSP), který přistupuje k správně nainstalovanému hardwarovému šifrovacímu zařízení.  Dostupnost zprostředkovatele CSP můžete ověřit kontrolou následujícího klíče registru pomocí Editoru registru (Regedit. exe): HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Podepisování dat pomocí karty klíčů  
  
1. Vytvořte novou instanci třídy <xref:System.Security.Cryptography.CspParameters>, předejte typ poskytovatele Integer a název poskytovatele do konstruktoru.  
  
2. Předejte příslušné příznaky do vlastnosti <xref:System.Security.Cryptography.CspParameters.Flags%2A> nově vytvořeného objektu <xref:System.Security.Cryptography.CspParameters>.  Například předejte příznak <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer>.  
  
3. Vytvořte novou instanci třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm> (například třídu <xref:System.Security.Cryptography.RSACryptoServiceProvider>) a předejte objekt <xref:System.Security.Cryptography.CspParameters> konstruktoru.  
  
4. Pomocí jedné z metod `Sign` podepište data a pomocí jedné z metod `Verify` Ověřte data.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Vygenerování náhodného čísla pomocí generátoru náhodných čísel hardwaru  
  
1. Vytvořte novou instanci třídy <xref:System.Security.Cryptography.CspParameters>, předejte typ poskytovatele Integer a název poskytovatele do konstruktoru.  
  
2. Vytvořte novou instanci <xref:System.Security.Cryptography.RNGCryptoServiceProvider>a předejte objekt <xref:System.Security.Cryptography.CspParameters> do konstruktoru.  
  
3. Pomocí metody <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> nebo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> Vytvořte náhodnou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak podepisovat data pomocí čipové karty.  Příklad kódu vytvoří objekt <xref:System.Security.Cryptography.CspParameters>, který zpřístupňuje čipovou kartu, a poté inicializuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pomocí zprostředkovatele CSP.  Příklad kódu pak podepisuje a ověřuje data.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Zahrňte <xref:System> a <xref:System.Security.Cryptography> obory názvů.  
  
- Musíte mít nainstalovanou čtečku čipových karet a ovladače nainstalované v počítači.  
  
- Objekt <xref:System.Security.Cryptography.CspParameters> musíte inicializovat pomocí informací, které jsou specifické pro vaše čtecí zařízení karet.  Další informace najdete v dokumentaci ke čtečce karet.
