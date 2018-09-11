---
title: 'Postupy: Použití ochrany dat'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b043c5a2173cff9eb82497f6d4ee8b7c0aa3f14c
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337925"
---
# <a name="how-to-use-data-protection"></a>Postupy: Použití ochrany dat
Rozhraní .NET Framework poskytuje přístup k data protection API (DPAPI), který umožňuje šifrování dat s využitím informací z aktuálního uživatelského účtu nebo počítači.  Pokud použijete rozhraní DPAPI, zmírnění náročný problém explicitně vygenerováním a uložením kryptografický klíč.  
  
 Použití <xref:System.Security.Cryptography.ProtectedMemory> třídy k zašifrování pole bajtů v paměti.  Tato funkce je dostupná v systému Microsoft Windows XP a novějších operačních systémech.  Můžete zadat, tato paměť se šifruje pomocí aktuálního procesu mohou ho dešifrovat aktuální proces pouze ze všech procesů, nebo stejný uživatelský kontext.  Zobrazit <xref:System.Security.Cryptography.MemoryProtectionScope> výčet podrobný popis <xref:System.Security.Cryptography.ProtectedMemory> možnosti.  
  
 Použití <xref:System.Security.Cryptography.ProtectedData> třídy k šifrování kopírování pole bajtů. Tato funkce je dostupná v systému Microsoft Windows 2000 a novějších operačních systémech.  Můžete určit, že je možné dešifrovat data zašifrovaná pomocí aktuálního uživatelského účtu jenom pomocí stejného uživatelského účtu, nebo můžete určit, že jakýkoli účet počítače, mohou ho dešifrovat data zašifrovaná pomocí aktuálního uživatelského účtu.  Zobrazit <xref:System.Security.Cryptography.DataProtectionScope> výčet podrobný popis <xref:System.Security.Cryptography.ProtectedData> možnosti.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>K šifrování dat v paměti s použitím ochrany dat  
  
1.  Zavolejte statickou <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> metoda při předávání pole bajtů, které mají šifrovat, entropie a ochranu rozsahu paměti.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>K dešifrování dat v paměti s použitím ochrany dat  
  
1.  Zavolejte statickou <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> metoda při předávání pole bajtů k dešifrování a ochranu rozsahu paměti.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Šifrování dat do souboru nebo datového proudu s použitím ochrany dat  
  
1.  Vytvořte náhodný entropie.  
  
2.  Zavolejte statickou <xref:System.Security.Cryptography.ProtectedData.Protect%2A> metoda při předávání pole bajtů, které mají šifrovat, entropie a rozsah dat ochrany.  
  
3.  Šifrovaná data zapište do souboru nebo datového proudu.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Dešifrování dat ze souboru nebo datového proudu s použitím ochrany dat  
  
1.  Přečtěte si šifrovaná data ze souboru nebo datového proudu.  
  
2.  Zavolejte statickou <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> metoda při předávání pole bajtů k dešifrování a rozsahu dat ochrany.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje dvě formy šifrování a dešifrování.  Příklad kódu nejprve šifruje a poté dešifruje v paměti pole bajtů.  V dalším kroku příklad kódu šifruje kopii bajtové pole, uloží ho do souboru, načte data zpět ze souboru a pak dešifruje data.  V příkladu se zobrazí původní data, šifrovaná data a dešifrovaná data.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zahrnout odkaz na `System.Security.dll`.  
  
-   Zahrnout <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, a <xref:System.Text> oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.ProtectedMemory>  
- <xref:System.Security.Cryptography.ProtectedData>
