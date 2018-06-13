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
ms.openlocfilehash: d04af38123efdbb70b8b917a3c4a59cb3a154262
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582184"
---
# <a name="how-to-use-data-protection"></a>Postupy: Použití ochrany dat
Rozhraní .NET Framework poskytuje přístup k data protection API (DPAPI), které umožňuje šifrování dat pomocí informací z aktuální uživatelský účet nebo počítači.  Pokud použijete rozhraní DPAPI, tím se obtížně problém explicitně generování a ukládání kryptografického klíče.  
  
 Použití <xref:System.Security.Cryptography.ProtectedMemory> třída k zašifrování pole bajtů v paměti.  Tato funkce je k dispozici v systému Microsoft Windows XP a novějších operačních systémech.  Můžete určit, že paměť šifrována pomocí aktuálního procesu mohou ho dešifrovat aktuální proces pouze všechny procesy, nebo ze stejného uživatelského kontextu.  Najdete v článku <xref:System.Security.Cryptography.MemoryProtectionScope> výčet podrobný popis <xref:System.Security.Cryptography.ProtectedMemory> možnosti.  
  
 Použití <xref:System.Security.Cryptography.ProtectedData> třída k zašifrování kopie pole bajtů. Tato funkce je k dispozici v systému Microsoft Windows 2000 a novějších operačních systémech.  Můžete zadat data zašifrovaná pomocí aktuální uživatelský účet je pak možné dešifrovat jenom pomocí stejného uživatelského účtu, nebo můžete zadat, že všechny účet v počítači, mohou ho dešifrovat data zašifrovaná pomocí aktuálního uživatelského účtu.  Najdete v článku <xref:System.Security.Cryptography.DataProtectionScope> výčet podrobný popis <xref:System.Security.Cryptography.ProtectedData> možnosti.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>K šifrování dat v paměti pomocí funkce Ochrana dat  
  
1.  Zavolejte statickou <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> metoda při předávání pole bajtů k šifrování, entropie a rozsahu ochrany paměti.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>K dešifrování dat v paměti pomocí funkce Ochrana dat  
  
1.  Zavolejte statickou <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> metoda při předávání pole bajtů k dešifrování a rozsahu ochrany paměti.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Šifrování dat do souboru nebo datového proudu s použitím ochrany dat  
  
1.  Vytvořte náhodné šifrování.  
  
2.  Zavolejte statickou <xref:System.Security.Cryptography.ProtectedData.Protect%2A> metoda při předávání pole bajtů k šifrování, entropie a rozsahu ochrany dat.  
  
3.  Šifrovaná data zapište do souboru nebo datový proud.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Dešifrování dat ze souboru nebo datového proudu s použitím ochrany dat  
  
1.  Čtení ze souboru nebo datový proud šifrovaná data.  
  
2.  Zavolejte statickou <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> metoda při předávání pole bajtů k dešifrování a rozsahu ochrany dat.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje dvě formy šifrování a dešifrování.  Příklad kódu nejprve šifruje a poté dešifruje pole bajtů v paměti.  V dalším kroku příkladu kódu šifruje kopii bajtové pole, uloží do souboru, načte data zpět ze souboru a poté dešifruje data.  Příklad zobrazí původní data, šifrovaná data a dešifrovaná data.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zahrnout odkaz na `System.Security.dll`.  
  
-   Zahrnout <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, a <xref:System.Text> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography.ProtectedMemory>  
 <xref:System.Security.Cryptography.ProtectedData>
