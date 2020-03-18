---
title: -recurse (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606751"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (Možnosti kompilátoru Jazyka C#)
Možnost -recurse umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích zadaného adresáře (dir) nebo adresáře projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir` (volitelné)  
 Adresář, ve kterém má hledání začít. Pokud není zadán, hledání začíná v adresáři projektu.  
  
 `file`  
 Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-recurse** umožňuje kompilovat soubory zdrojového kódu ve všech`dir`podřízených adresářích zadaného adresáře ( ) nebo adresáře projektu.  
  
 Zástupné znaky v názvu souboru můžete použít ke kompilaci všech odpovídajících souborů v adresáři projektu bez použití **-recurse**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.  
  
## <a name="example"></a>Příklad  
 Zkompiluje všechny soubory jazyka C# v aktuálním adresáři:  
  
```console  
csc *.cs  
```  
  
 Zkompiluje všechny soubory jazyka C# v adresáři dir1\dir2 a všechny adresáře pod ním a generuje dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
