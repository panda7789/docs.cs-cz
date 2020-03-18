---
title: -target:exe (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606464"
---
# <a name="-targetexe-c-compiler-options"></a>-target:exe (Možnosti kompilátoru Jazyka C#)
Možnost **-target:exe** způsobí, že kompilátor vytvoří spustitelný soubor (EXE), konzolovou aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-target:exe** je ve výchozím nastavení účinná. Spustitelný soubor bude vytvořen s příponou EXE.  
  
 Použijte [-target:winexe](./target-winexe-compiler-option.md) k vytvoření spustitelného souboru programu systému Windows.  
  
 Pokud není uvedeno jinak s volbou [-out,](./out-compiler-option.md) název výstupního souboru přebírá název vstupního souboru, který obsahuje [metodu Main.](../../programming-guide/main-and-command-args/index.md)  
  
 Pokud jsou zadány na příkazovém řádku, všechny soubory až do další **volby -out** nebo **-target:module** se používají k vytvoření souboru EXE  
  
 V souborech zdrojového kódu, které jsou zkompilovány do souboru EXE, je vyžadována jedna metoda **Main.** [-main](./main-compiler-option.md) kompilátor možnost umožňuje určit, která třída obsahuje **Main** metoda, v případech, kdy váš kód má více než jednu třídu s **Main** metoda.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Aplikace.**  
  
3. Upravte vlastnost **Output type.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Každý z následujících příkazových řádků se zkompiluje `in.cs`a vytvoří `in.exe`:  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-target (Možnosti kompilátoru Jazyka C#)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
