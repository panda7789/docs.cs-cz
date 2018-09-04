---
title: -recurse (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 1fc5591cb73164e15384eb4407a6e61e903eedbb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529894"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (možnosti kompilátoru C#)
-Recurse – možnost umožňuje kompilaci souborů zdrojového kódu ve všech adresářích podřízené zadaný adresář (adresář) nebo adresáře projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir` (volitelné)  
 Adresář, ve kterém chcete, aby hledání začalo. Pokud není zadaný, hledání začne v adresáři projektu.  
  
 `file`  
 Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 **-Recurse** možnost umožňuje kompilaci souborů zdrojového kódu ve všech adresářích podřízené zadaného adresáře (`dir`) nebo adresáře projektu.  
  
 Zástupné znaky v názvu souboru můžete použít ke kompilaci všech odpovídajících souborů v adresáři projektu bez použití **-recurse**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="example"></a>Příklad  
 Kompiluje všechny soubory jazyka C# v aktuálním adresáři:  
  
```console  
csc *.cs  
```  
  
 Kompiluje se všechny soubory jazyka C# v adresáři dir1\dir2 a všechny adresáře pod ní a generuje dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
