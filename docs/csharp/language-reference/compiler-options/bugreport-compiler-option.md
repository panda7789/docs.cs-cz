---
description: -bugreport – (možnosti kompilátoru C#)
title: -bugreport – (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 2c358b2dda400f6077ffb5ba1dfc8e6e1127fa52
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125992"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport – (možnosti kompilátoru C#)
Určuje, že informace o ladění by měly být umístěny do souboru pro pozdější analýzu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Název souboru, který má obsahovat zprávu o chybě.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-bugreport –** určuje, že se mají umístit následující informace `file` :  
  
- Kopie všech souborů zdrojového kódu v kompilaci.  
  
- Seznam možností kompilátoru použitých v kompilaci.  
  
- Informace o verzi kompilátoru, době běhu a operačním systému.  
  
- Odkazovaná sestavení a moduly uložené jako šestnáctkové číslice, s výjimkou sestavení, která jsou dodávána s .NET Framework a sadou SDK.  
  
- Výstup kompilátoru, pokud existuje.  
  
- Popis problému, ke kterému se zobrazí výzva.  
  
- Popis toho, jak si myslíte problém, by měl být opravený, na který se zobrazí výzva.  
  
 Pokud se tato možnost používá s parametrem **-errorreport: prompt** nebo **-errorreport: Send**, informace v souboru se odešlou společnosti Microsoft Corporation.  
  
 Vzhledem k tomu, že se kopie všech souborů zdrojového kódu umístí do `file` , může být vhodné reprodukce podezřelého kódu reprodukována v co nejkratším možném programu.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
 Všimněte si, že obsah generovaného souboru zveřejňuje zdrojový kód, který by mohl vést k neúmyslnému zpřístupnění informací.  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [-errorreport (možnosti kompilátoru C#)](./errorreport-compiler-option.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
