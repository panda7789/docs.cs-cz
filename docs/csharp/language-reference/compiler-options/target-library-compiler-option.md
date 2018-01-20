---
title: "-target: library (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 242f8ada7cbffc4a6986339d28c4284b50afca25
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-targetlibrary-c-compiler-options"></a>-target: library (možnosti kompilátoru C#)
**-Target: library** možnost způsobí, že kompilátor vytvoří dynamická knihovna (DLL) namísto spustitelného souboru (EXE).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Poznámky  
 Knihovnu DLL, bude vytvořena s příponou .dll.  
  
 Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název prvního vstupního souboru.  
  
 Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **-out** nebo **-target: module** možnost slouží k vytvoření souboru .dll.  
  
 Při vytváření souboru .dll [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda se nevyžaduje.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **aplikace** stránku vlastností.  
  
3.  Změnit **výstupní typ** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs`, vytváření `in.dll`:  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
