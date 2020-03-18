---
title: -pdb (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602574"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (Možnosti kompilátoru Jazyka C#)
Možnost kompilátoru **-pdb** určuje název a umístění souboru ladicích symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Název a umístění souboru ladicích symbolů.  
  
## <a name="remarks"></a>Poznámky  
 Když zadáte [-debug (C# Compiler Options),](./debug-compiler-option.md)kompilátor vytvoří soubor PDB ve stejném adresáři, kde kompilátor vytvoří výstupní soubor (.exe nebo .dll) s názvem souboru, který je stejný jako název výstupního souboru.  
  
 **-pdb** umožňuje zadat název a umístění souboru PDB, který není výchozí.  
  
 Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani ji nelze programově změnit.  
  
## <a name="example"></a>Příklad  
 Kompilace `t.cs` a vytvoření souboru PDB s názvem tt.pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
