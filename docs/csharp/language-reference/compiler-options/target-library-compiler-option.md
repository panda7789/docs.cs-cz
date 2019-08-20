---
title: '-target: Library (C# možnosti kompilátoru)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606390"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target: Library (C# možnosti kompilátoru)
Možnost **-target: Library** způsobí, že kompilátor vytvoří dynamickou knihovnu (DLL) místo spustitelného souboru (exe).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Poznámky  
 Knihovna DLL bude vytvořena s příponou. dll.  
  
 Pokud není uvedeno jinak s možností [-out](./out-compiler-option.md) , název výstupního souboru vezme název prvního vstupního souboru.  
  
 Při zadání na příkazovém řádku všechny soubory až do možnosti další **-mimo** **cíl: modul** slouží k vytvoření souboru. dll.  
  
 Při sestavování souboru. dll není metoda [Main](../../programming-guide/main-and-command-args/index.md) nutná.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **Typ výstupu** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.OutputType%2A>v tématu.  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs`, vytvořit `in.dll`:  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-Target (C# možnosti kompilátoru)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
