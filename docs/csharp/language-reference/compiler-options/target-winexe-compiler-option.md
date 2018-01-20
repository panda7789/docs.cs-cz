---
title: "-target: winexe (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b13af4e665a2bf5a75472bc8f4a501e90c59281a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-targetwinexe-c-compiler-options"></a>-target: winexe (možnosti kompilátoru C#)
**-Target: winexe** možnost způsobí, že kompilátor vytvoří spustitelný soubor (EXE), programu systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří se spustitelný soubor s příponou .exe. Windows program je ten, který poskytuje uživatelské rozhraní z knihovny rozhraní .NET Framework nebo s rozhraními API Win32.  
  
 Použití [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) k vytvoření konzolové aplikace.  
  
 Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.  
  
 Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **-out** nebo [-cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možnost slouží k vytvoření programu systému Windows.  
  
 Pouze jeden **hlavní** metoda je vyžadována v soubory zdrojového kódu, které jsou zkompilovány do souboru s příponou .exe. [– Hlavní](../../../csharp/language-reference/compiler-options/main-compiler-option.md) možnost umožňuje zadat, která třída obsahuje **hlavní** metoda v případech, kdy váš kód obsahuje více než jednu třídu s **hlavní** metoda.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **aplikace** stránku vlastností.  
  
3.  Změnit **výstupní typ** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` do programu systému Windows:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
