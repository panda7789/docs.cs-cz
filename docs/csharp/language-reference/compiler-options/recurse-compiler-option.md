---
description: -rekurze (možnosti kompilátoru C#)
title: -rekurze (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 3edd7e23358bc0569dae6204d519209df1ade290
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124822"
---
# <a name="-recurse-c-compiler-options"></a>-rekurze (možnosti kompilátoru C#)
Možnost-rekurze umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře (dir), nebo adresáře projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir` (volitelné)  
 Adresář, ve kterém chcete zahájit hledání. Pokud tento parametr nezadáte, hledání začne v adresáři projektu.  
  
 `file`  
 Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-rekurze** umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře ( `dir` ), nebo adresáře projektu.  
  
 Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bez použití **rekurze**.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="example"></a>Příklad  
 Zkompiluje všechny soubory v jazyce C# v aktuálním adresáři:  
  
```console  
csc *.cs  
```  
  
 Zkompiluje všechny soubory v jazyce C# v adresáři dir1\dir2 a všech adresářích pod ním a vygeneruje dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
