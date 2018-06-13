---
title: -bugreport (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 5505971ad9a6920124dd4d8c12642a5e4e346322
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214089"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (možnosti kompilátoru C#)
Určuje, že informace o ladění mají být umístěny v souboru pro pozdější analýzu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Název souboru, který má obsahovat sestavy chyb.  
  
## <a name="remarks"></a>Poznámky  
 **- Bugreport** možnost určuje, že tyto informace mají být umístěny v `file`:  
  
-   Kopírovat všechny soubory zdrojového kódu v kompilace.  
  
-   Seznam možností kompilátoru použita při kompilaci.  
  
-   Informace o verzi o kompilátoru, běhu a operačního systému.  
  
-   Odkazovaná sestavení a moduly, které jsou uloženy jako šestnáctkové číslice, s výjimkou sestavení, které jsou dodávány pomocí rozhraní .NET Framework a sady SDK.  
  
-   Výstup kompilátoru, pokud existuje.  
  
-   Popis problému, který jste vyzváni k.  
  
-   Popis jak domníváte, že problém je třeba stanovit, které jste vyzváni k.  
  
 Pokud tato možnost se používá s **- errorreport: řádku** nebo **- errorreport: Odeslat**, informace v souboru budou odeslány společnosti Microsoft Corporation.  
  
 Protože kopii všechny soubory zdrojového kódu budou umístěny v `file`, můžete chtít reprodukovat možného kód do nejkratší programu.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
 Všimněte si, že obsah vygenerovaný soubor vystavit zdrojový kód, který by mohl vést k neúmyslnému zpřístupnění informací.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [-errorreport (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
