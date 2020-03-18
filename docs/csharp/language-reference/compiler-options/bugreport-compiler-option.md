---
title: -bugreport (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603078"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (C# Možnosti kompilátoru)
Určuje, že informace o ladění by měly být umístěny do souboru pro pozdější analýzu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Název souboru, který má obsahovat hlášení o chybě.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-bugreport** určuje, že následující informace `file`by měly být umístěny v :  
  
- Kopie všech souborů zdrojového kódu v kompilaci.  
  
- Seznam možností kompilátoru použitých v kompilaci.  
  
- Informace o verzi kompilátoru, běhu a operačním systému.  
  
- Odkazovaná sestavení a moduly uložené jako šestnáctkové číslice s výjimkou sestavení, která jsou dodávána s rozhraním .NET Framework a SadM SDK.  
  
- Výstup kompilátoru, pokud existuje.  
  
- Popis problému, ke kterému budete vyzváni.  
  
- Popis toho, jak si myslíte, že by měl být problém opraven, k jakému budete vyzváni.  
  
 Pokud je tato možnost použita s **-errorreport:prompt** nebo **-errorreport:send**, budou informace v souboru odeslány společnosti Microsoft Corporation.  
  
 Vzhledem k tomu, že kopie `file`všech souborů zdrojového kódu bude umístěna do aplikace , můžete chtít reprodukovat podezřelou vadu kódu v co nejkratším možném programu.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.  
  
 Všimněte si, že obsah generovaného souboru vystavit zdrojový kód, který by mohl mít za následek neúmyslné zpřístupnění informací.  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [-errorreport (Možnosti kompilátoru Jazyka C#)](./errorreport-compiler-option.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
