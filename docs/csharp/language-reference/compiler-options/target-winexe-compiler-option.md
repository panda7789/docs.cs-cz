---
title: '-target: winexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 3c16bf8aed0d281b2b5a3f9c6ae06f343b1eff7c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307303"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target: winexe (možnosti kompilátoru C#)
**-Target: winexe** možnost způsobí, že kompilátor vytvoří spustitelný soubor (EXE), Windows program.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří se spustitelný soubor s příponou .exe. Windows program je ten, který poskytuje uživatelské rozhraní z knihovny rozhraní .NET Framework nebo s rozhraními API pro Windows.  
  
 Použití [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) k vytvoření konzolové aplikace.  
  
 Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) – metoda.  
  
 Pokud je zadán v příkazovém řádku, všechny soubory až do další **-out** nebo [– cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) slouží k vytvoření programu Windows.  
  
 Pouze jeden **hlavní** metoda je vyžadována v souborech zdrojového kódu, které jsou kompilovány do souboru s příponou .exe. [– Hlavní](../../../csharp/language-reference/compiler-options/main-compiler-option.md) možnost umožňuje zadat, která třída obsahuje **hlavní** metoda v případech, kdy váš kód obsahuje víc než jedna třída s **hlavní** – metoda.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete v projektu **vlastnosti** stránky.  
  
2. Klikněte na tlačítko **aplikace** stránku vlastností.  
  
3. Upravit **typ výstupu** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` do aplikace Windows:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
