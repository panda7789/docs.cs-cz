---
title: 'Postupy: Použití ochrany dat'
description: Naučte se používat ochranu dat pomocí přístupu k rozhraní data Protection API (DPAPI) v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598590"
---
# <a name="how-to-use-data-protection"></a>Postupy: Použití ochrany dat
.NET Framework poskytuje přístup k rozhraní data Protection API (DPAPI), které umožňuje šifrovat data pomocí informací z aktuálního uživatelského účtu nebo počítače.  Při použití rozhraní DPAPI je obtížné vyřešit obtížně generovaný a uložený kryptografický klíč.  
  
 Použijte <xref:System.Security.Cryptography.ProtectedMemory> třídu k zašifrování pole bajtů v paměti.  Tato funkce je k dispozici v systému Microsoft Windows XP a novějších operačních systémech.  Můžete určit, že paměť zašifrovaná pomocí aktuálního procesu může být dešifrována pouze aktuálním procesem, všemi procesy nebo ze stejného kontextu uživatele.  <xref:System.Security.Cryptography.MemoryProtectionScope>Podrobný popis možností najdete v části výčet <xref:System.Security.Cryptography.ProtectedMemory> .  
  
 Použijte <xref:System.Security.Cryptography.ProtectedData> třídu k zašifrování kopie pole bajtů. Tato funkce je k dispozici v systému Microsoft Windows 2000 a novějších operačních systémech.  Můžete určit, že data zašifrovaná pomocí aktuálního uživatelského účtu je možné dešifrovat jenom stejným uživatelským účtem, nebo můžete zadat, aby se data zašifrovaná aktuálním uživatelským účtem mohla dešifrovat jakýmkoli účtem v počítači.  <xref:System.Security.Cryptography.DataProtectionScope>Podrobný popis možností najdete v části výčet <xref:System.Security.Cryptography.ProtectedData> .  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Šifrování dat v paměti pomocí ochrany dat  
  
1. Volejte statickou <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> metodu při předávání pole bajtů k zašifrování, entropii a rozsahu ochrany paměti.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Dešifrování dat v paměti pomocí ochrany dat  
  
1. Volejte statickou <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> metodu při předávání pole bajtů k dešifrování a rozsahu ochrany paměti.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Šifrování dat do souboru nebo datového proudu pomocí ochrany dat  
  
1. Vytvořte náhodnou entropii.  
  
2. Volejte statickou <xref:System.Security.Cryptography.ProtectedData.Protect%2A> metodu při předávání pole bajtů k zašifrování, entropii a rozsahu ochrany dat.  
  
3. Zapište zašifrovaná data do souboru nebo datového proudu.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Dešifrování dat ze souboru nebo datového proudu pomocí ochrany dat  
  
1. Přečtěte si šifrovaná data ze souboru nebo datového proudu.  
  
2. Volejte statickou <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> metodu při předávání pole bajtů k dešifrování a rozsahu ochrany dat.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje dvě formy šifrování a dešifrování.  Nejprve příklad kódu šifruje a pak dešifruje pole bajtů v paměti.  V dalším příkladu kód zašifruje kopii pole bajtů, uloží ho do souboru, načte data zpátky ze souboru a pak data dešifruje.  V příkladu se zobrazí původní data, šifrovaná data a dešifrovaná data.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Přidejte odkaz na `System.Security.dll` .  
  
- Přidejte <xref:System> <xref:System.IO> obor názvů,, <xref:System.Security.Cryptography> a <xref:System.Text> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
