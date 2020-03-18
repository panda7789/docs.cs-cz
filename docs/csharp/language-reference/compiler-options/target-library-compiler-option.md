---
title: -target:library (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606390"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target:library (C# Možnosti kompilátoru)
Možnost **-target:library** způsobí, že kompilátor vytvoří knihovnu dynamických vazeb (DLL) spíše než spustitelný soubor (EXE).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Poznámky  
 DLL bude vytvořena s rozšířením .dll.  
  
 Pokud není u možnosti [-out](./out-compiler-option.md) uvedeno jinak, název výstupního souboru převezme název prvního vstupního souboru.  
  
 Pokud je zadán na příkazovém řádku, všechny soubory až do další **-out** nebo **-target:module** možnost se používají k vytvoření souboru DLL.  
  
 Při vytváření souboru DLL není vyžadována metoda [Main.](../../programming-guide/main-and-command-args/index.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Aplikace.**  
  
3. Upravte vlastnost **Output type.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` `in.dll`, vytváření :  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-target (Možnosti kompilátoru Jazyka C#)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
