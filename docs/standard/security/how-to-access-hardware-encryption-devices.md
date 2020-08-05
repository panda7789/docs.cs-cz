---
title: 'Postupy: Přístup k hardwarovým šifrovacím zařízením'
ms.date: 07/14/2020
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
ms.openlocfilehash: 7cd3aab80a8388c1d4ce08e4ae94aae84cfff239
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557135"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Postupy: Přístup k hardwarovým šifrovacím zařízením

> [!NOTE]
> Tento článek se týká systému Windows.

<xref:System.Security.Cryptography.CspParameters>Pro přístup k hardwarovým šifrovacím zařízením můžete použít třídu. Tuto třídu můžete například použít k integraci aplikace s čipovou kartou, generátor náhodných čísel hardwaru nebo implementaci hardwaru konkrétního šifrovacího algoritmu.  

<xref:System.Security.Cryptography.CspParameters>Třída vytvoří zprostředkovatele kryptografických služeb (CSP), který přistupuje k správně nainstalovanému hardwarovému šifrovacímu zařízení.  Dostupnost zprostředkovatele CSP můžete ověřit kontrolou následujícího klíče registru pomocí Editoru registru (Regedit.exe): HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Podepisování dat pomocí karty klíčů  
  
1. Vytvořte novou instanci <xref:System.Security.Cryptography.CspParameters> třídy, předejte typ poskytovatele Integer a název poskytovatele do konstruktoru.  
  
2. Předejte příslušné příznaky do <xref:System.Security.Cryptography.CspParameters.Flags%2A> vlastnosti nově vytvořeného <xref:System.Security.Cryptography.CspParameters> objektu.  Například předejte <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> příznak.  
  
3. Vytvořte novou instanci <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (například <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy) a předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.  
  
4. Podepište data pomocí jedné z `Sign` metod a ověřte data pomocí jedné z `Verify` metod.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Vygenerování náhodného čísla pomocí generátoru náhodných čísel hardwaru  
  
1. Vytvořte novou instanci <xref:System.Security.Cryptography.CspParameters> třídy, předejte typ poskytovatele Integer a název poskytovatele do konstruktoru.  
  
2. Vytvořte novou instanci <xref:System.Security.Cryptography.RNGCryptoServiceProvider> objektu a předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.  
  
3. Vytvořte náhodnou hodnotu pomocí <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> metody nebo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> .  
  
## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak podepisovat data pomocí čipové karty.  Příklad kódu vytvoří <xref:System.Security.Cryptography.CspParameters> objekt, který zpřístupňuje čipovou kartu, a poté inicializuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pomocí CSP.  Příklad kódu pak podepisuje a ověřuje data.  

Z důvodu kolizí problémů se SHA1 doporučujeme SHA256 nebo lepší.
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Přidejte <xref:System> <xref:System.Security.Cryptography> obory názvů a.  
  
- Musíte mít nainstalovanou čtečku čipových karet a ovladače nainstalované v počítači.  
  
- Je nutné inicializovat <xref:System.Security.Cryptography.CspParameters> objekt s použitím informací, které jsou specifické pro vaše čtecí zařízení karet.  Další informace najdete v dokumentaci ke čtečce karet.

## <a name="see-also"></a>Viz také

- [Kryptografický model](cryptography-model.md)
- [Šifrovací služby](cryptographic-services.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
