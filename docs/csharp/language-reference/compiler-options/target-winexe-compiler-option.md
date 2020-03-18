---
title: -target:winexe (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606379"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target:winexe (Možnosti kompilátoru Jazyka C#)
Možnost **-target:winexe** způsobí, že kompilátor vytvoří spustitelný soubor (EXE), program systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Spustitelný soubor bude vytvořen s příponou EXE. Program systému Windows je program, který poskytuje uživatelské rozhraní z knihovny rozhraní .NET Framework nebo s rozhraními API systému Windows.  
  
 Použijte [-target:exe](./target-exe-compiler-option.md) k vytvoření konzolové aplikace.  
  
 Pokud není uvedeno jinak s volbou [-out,](./out-compiler-option.md) název výstupního souboru přebírá název vstupního souboru, který obsahuje [metodu Main.](../../programming-guide/main-and-command-args/index.md)  
  
 Pokud jsou zadány na příkazovém řádku, všechny soubory až do další **-out** nebo [-target](./target-compiler-option.md) možnost jsou použity k vytvoření programu systému Windows.  
  
 V souborech zdrojového kódu, které jsou zkompilovány do souboru EXE, je vyžadována jedna metoda **Main.** [-main](./main-compiler-option.md) Možnost umožňuje určit, která třída obsahuje **Main** metoda, v případech, kdy váš kód má více než jednu třídu s **Main** metoda.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Aplikace.**  
  
3. Upravte vlastnost **Output type.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` do programu systému Windows:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-target (Možnosti kompilátoru Jazyka C#)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
