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
ms.openlocfilehash: f25455fac84903f9c39861e1f6863f6b2f6928f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587393"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (možnosti kompilátoru C#)
Určuje, že informace o ladění by měly být umístěny v souboru pro pozdější analýzu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Název souboru, který má obsahovat hlášení o chybě.  
  
## <a name="remarks"></a>Poznámky  
 **- Bugreport** možnost určuje, že tyto informace mají být umístěny v `file`:  
  
- Kopírování všech souborů zdrojového kódu dané kompilace.  
  
- Seznam možností kompilátoru použita při kompilaci.  
  
- Informace o verzi kompilátoru, běhu a operačního systému.  
  
- Odkazovaná sestavení a modulů, které jsou uloženy jako šestnáctkové číslice, s výjimkou sestavení, které se dodávají pomocí rozhraní .NET Framework a sady SDK.  
  
- Výstup kompilátoru, pokud existuje.  
  
- Popis problému, který zobrazí se výzva k zadání.  
  
- Popis jak domníváte, že problém je třeba stanovit, která vám zobrazí výzva k zadání.  
  
 Pokud tato možnost se používá s **- errorreport: řádku** nebo **- errorreport: Odeslat**, informace v souboru se odešlou do Microsoft Corporation.  
  
 Vzhledem k tomu, že kopie všech souborů zdrojového kódu budou umístěny v `file`, můžete chtít reprodukovat v nejkratší možné aplikaci podezřelý kód.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
 Všimněte si, že obsah generovaný soubor vystavit zdrojový kód, který může dojít k neúmyslnému zpřístupnění informací.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [-errorreport (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
