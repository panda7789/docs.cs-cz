---
description: '-target: Library (možnosti kompilátoru C#)'
title: '-target: Library (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 953249c4d0168ed3d279d03a0b2fb63d8ff6d5f5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128475"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target: Library (možnosti kompilátoru C#)
Možnost **-target: Library** způsobí, že kompilátor vytvoří dynamickou knihovnu (DLL) místo spustitelného souboru (exe).  
  
## <a name="syntax"></a>Syntax  
  
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
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs` , vytvořit `in.dll` :  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-Target (možnosti kompilátoru C#)](./target-compiler-option.md)
- [Možnosti kompilátoru C#](./index.md)
