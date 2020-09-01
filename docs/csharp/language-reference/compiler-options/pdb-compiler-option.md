---
description: -PDB (možnosti kompilátoru C#)
title: -PDB (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 0dcafd0fd260488922c74a2330b312e80467e779
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124913"
---
# <a name="-pdb-c-compiler-options"></a>-PDB (možnosti kompilátoru C#)
Možnost kompilátoru **-PDB** Určuje název a umístění souboru se symboly ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Název a umístění souboru se symboly ladění.  
  
## <a name="remarks"></a>Poznámky  
 Zadáte-li parametr [-Debug (možnosti kompilátoru C#)](./debug-compiler-option.md), kompilátor vytvoří soubor. pdb ve stejném adresáři, ve kterém kompilátor vytvoří výstupní soubor (. exe nebo. dll) s názvem souboru, který je stejný jako název výstupního souboru.  
  
 **-PDB** umožňuje zadat jiný než výchozí název souboru a umístění pro soubor. pdb.  
  
 Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani jej nelze změnit programově.  
  
## <a name="example"></a>Příklad  
 Zkompilujte `t.cs` a vytvořte soubor. pdb s názvem TT. pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
