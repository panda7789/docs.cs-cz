---
title: -bugreport – (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603078"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport – (C# možnosti kompilátoru)
Určuje, že informace o ladění by měly být umístěny do souboru pro pozdější analýzu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Název souboru, který má obsahovat zprávu o chybě.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-bugreport –** určuje, že se mají umístit `file`následující informace:  
  
- Kopie všech souborů zdrojového kódu v kompilaci.  
  
- Seznam možností kompilátoru použitých v kompilaci.  
  
- Informace o verzi kompilátoru, době běhu a operačním systému.  
  
- Odkazovaná sestavení a moduly uložené jako šestnáctkové číslice, s výjimkou sestavení, která jsou dodávána s .NET Framework a sadou SDK.  
  
- Výstup kompilátoru, pokud existuje.  
  
- Popis problému, ke kterému se zobrazí výzva.  
  
- Popis toho, jak si myslíte problém, by měl být opravený, na který se zobrazí výzva.  
  
 Pokud se tato možnost používá s parametrem **-errorreport: prompt** nebo **-errorreport: Send**, informace v souboru se odešlou společnosti Microsoft Corporation.  
  
 Vzhledem k tomu, že se kopie všech souborů zdrojového kódu umístí `file`do, může být vhodné reprodukce podezřelého kódu reprodukována v co nejkratším možném programu.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
 Všimněte si, že obsah generovaného souboru zveřejňuje zdrojový kód, který by mohl vést k neúmyslnému zpřístupnění informací.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [-errorreport (C# možnosti kompilátoru)](./errorreport-compiler-option.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
