---
title: "-recurse (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b50454112bc7aee6c3e0f8fe674e8727ca9e49be
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-recurse-c-compiler-options"></a>-recurse (možnosti kompilátoru C#)
-Recurse – možnost umožňuje kompilovat soubory zdrojového kódu ve všech zadaný adresář (dir) nebo adresáři projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`(volitelné)  
 Adresář, ve kterém chcete vyhledávání začít. Pokud není tento parametr zadán, začne vyhledávání v adresáři projektu.  
  
 `file`  
 Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 **-Recurse** možnost umožňuje zkompilovat soubory zdrojového kódu ve všech zadaného adresáře (`dir`) nebo adresáře projektu.  
  
 Můžete použít zástupné znaky v názvu souboru pro kompilaci všechny odpovídající soubory v adresáři projektu bez použití **-recurse**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="example"></a>Příklad  
 Kompiluje všechny soubory C# v aktuálním adresáři:  
  
```console  
csc *.cs  
```  
  
 Kompiluje všechny soubory C# v adresáři dir1\dir2 a všech adresářích pod ním a generuje dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
