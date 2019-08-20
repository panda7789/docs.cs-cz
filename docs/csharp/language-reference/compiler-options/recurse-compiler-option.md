---
title: -rekurzeC# (možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606751"
---
# <a name="-recurse-c-compiler-options"></a>-rekurzeC# (možnosti kompilátoru)
Možnost-rekurze umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře (dir), nebo adresáře projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`volitelné  
 Adresář, ve kterém chcete zahájit hledání. Pokud tento parametr nezadáte, hledání začne v adresáři projektu.  
  
 `file`  
 Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-** rekurze umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře (`dir`), nebo adresáře projektu.  
  
 Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bezpoužití rekurze.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="example"></a>Příklad  
 Zkompiluje všechny C# soubory v aktuálním adresáři:  
  
```console  
csc *.cs  
```  
  
 Zkompiluje všechny C# soubory v adresáři dir1\dir2 a všech adresářích pod ním a vygeneruje dir2. dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
