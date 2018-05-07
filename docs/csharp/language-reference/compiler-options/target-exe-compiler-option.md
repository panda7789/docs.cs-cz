---
title: '-target: exe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 194e4f7efaebd9523791090bcab09c019f8554a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-targetexe-c-compiler-options"></a>-target: exe (možnosti kompilátoru C#)
**-Target: exe** možnost způsobí, že kompilátor vytvořit spustitelný soubor (EXE), konzolová aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Poznámky  
 **-Target: exe** možnost ve výchozím nastavení je v platnosti. Vytvoří se spustitelný soubor s příponou .exe.  
  
 Použití [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) pro vytvoření spustitelného souboru programu systému Windows.  
  
 Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.  
  
 Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **-out** nebo **-target: module** možnost slouží k vytvoření souboru .exe  
  
 Pouze jeden **hlavní** metoda je vyžadována v soubory zdrojového kódu, které jsou zkompilovány do souboru s příponou .exe. [– Hlavní](../../../csharp/language-reference/compiler-options/main-compiler-option.md) – možnost kompilátoru umožňuje určit, která třída obsahuje **hlavní** metoda v případech, kdy váš kód obsahuje více než jednu třídu s **hlavní** metoda.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **aplikace** stránku vlastností.  
  
3.  Změnit **výstupní typ** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Každý z následujících příkazových řádků zkompiluje `in.cs`, vytváření `in.exe`:  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
