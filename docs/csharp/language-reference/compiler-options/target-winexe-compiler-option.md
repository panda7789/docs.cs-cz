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
ms.openlocfilehash: f77137e3cc2f734435d3b1d391a303fcd3e16332
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468836"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target: winexe (možnosti kompilátoru C#)
**-Target: winexe** možnost způsobí, že kompilátor vytvoří spustitelný soubor (EXE), Windows program.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří se spustitelný soubor s příponou .exe. Windows program je ten, který poskytuje uživatelské rozhraní z knihovny rozhraní .NET Framework nebo pomocí rozhraní API systému Win32.  
  
 Použití [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) k vytvoření konzolové aplikace.  
  
 Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) – metoda.  
  
 Pokud je zadán v příkazovém řádku, všechny soubory až do další **-out** nebo [– cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) slouží k vytvoření programu Windows.  
  
 Pouze jeden **hlavní** metoda je vyžadována v souborech zdrojového kódu, které jsou kompilovány do souboru s příponou .exe. [– Hlavní](../../../csharp/language-reference/compiler-options/main-compiler-option.md) možnost umožňuje zadat, která třída obsahuje **hlavní** metoda v případech, kdy váš kód obsahuje víc než jedna třída s **hlavní** – metoda.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **aplikace** stránku vlastností.  
  
3.  Upravit **typ výstupu** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` do aplikace Windows:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
