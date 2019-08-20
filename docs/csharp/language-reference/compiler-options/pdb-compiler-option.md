---
title: -PDB (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602574"
---
# <a name="-pdb-c-compiler-options"></a>-PDB (C# možnosti kompilátoru)
Možnost kompilátoru **-PDB** Určuje název a umístění souboru se symboly ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název a umístění souboru se symboly ladění.  
  
## <a name="remarks"></a>Poznámky  
 Zadáte-li parametr [-C# Debug (možnosti kompilátoru)](./debug-compiler-option.md), kompilátor vytvoří soubor. pdb ve stejném adresáři, ve kterém kompilátor vytvoří výstupní soubor (. exe nebo. dll) s názvem souboru, který je stejný jako název výstupního souboru.  
  
 **-PDB** umožňuje zadat jiný než výchozí název souboru a umístění pro soubor. pdb.  
  
 Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani jej nelze změnit programově.  
  
## <a name="example"></a>Příklad  
 Zkompilujte `t.cs` a vytvořte soubor. pdb s názvem TT. pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
