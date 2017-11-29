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
ms.openlocfilehash: a053e5676b10de3bd2eecf6de8be7a30329962af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="recurse-c-compiler-options"></a>/recurse (Možnosti kompilátoru C#)
Možnost/recurse umožňuje zkompilovat soubory zdrojového kódu ve všech zadaný adresář (dir) nebo adresáři projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`(volitelné)  
 Adresář, ve kterém chcete vyhledávání začít. Pokud není tento parametr zadán, začne vyhledávání v adresáři projektu.  
  
 `file`  
 Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 **/Recurse** možnost umožňuje zkompilovat soubory zdrojového kódu ve všech zadaného adresáře (`dir`) nebo adresáře projektu.  
  
 Můžete použít zástupné znaky v názvu souboru pro kompilaci všechny odpovídající soubory v adresáři projektu bez použití **/recurse**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="example"></a>Příklad  
 Kompiluje všechny soubory C# v aktuálním adresáři:  
  
```console  
csc *.cs  
```  
  
 Kompiluje všechny soubory C# v adresáři dir1\dir2 a všech adresářích pod ním a generuje dir2.dll:  
  
```console  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
