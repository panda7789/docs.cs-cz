---
title: 'Postupy: Použití ochrany dat'
description: Naučte se používat ochranu dat pomocí přístupu k rozhraní data Protection API (DPAPI) v rozhraní .NET.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: 263a07ddf357734e819fffdd41cdff60657adf15
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557057"
---
# <a name="how-to-use-data-protection"></a>Postupy: Použití ochrany dat

> [!NOTE]
> Tento článek se týká systému Windows.
>
> Informace o ASP.NET Core najdete v tématu [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).

Rozhraní .NET poskytuje přístup k rozhraní data Protection API (DPAPI), které umožňuje šifrovat data pomocí informací z aktuálního uživatelského účtu nebo počítače.  Při použití rozhraní DPAPI je obtížné vyřešit obtížně generovaný a uložený kryptografický klíč.  
  
Použijte <xref:System.Security.Cryptography.ProtectedData> třídu k zašifrování kopie pole bajtů. Tato funkce je k dispozici v .NET Framework, .NET Core a .NET 5.  Můžete určit, že data zašifrovaná pomocí aktuálního uživatelského účtu je možné dešifrovat jenom stejným uživatelským účtem, nebo můžete zadat, aby se data zašifrovaná aktuálním uživatelským účtem mohla dešifrovat jakýmkoli účtem v počítači.  <xref:System.Security.Cryptography.DataProtectionScope>Podrobný popis možností najdete v části výčet <xref:System.Security.Cryptography.ProtectedData> .  
  
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

Tento příklad se zkompiluje a spustí pouze v případě, že cílíte .NET Framework a běží v systému Windows.

- Přidejte odkaz na `System.Security.dll` .  
  
- Přidejte <xref:System> <xref:System.IO> obor názvů,, <xref:System.Security.Cryptography> a <xref:System.Text> .  
  
## <a name="see-also"></a>Viz také

- [Kryptografický model](cryptography-model.md)
- [Šifrovací služby](cryptographic-services.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
