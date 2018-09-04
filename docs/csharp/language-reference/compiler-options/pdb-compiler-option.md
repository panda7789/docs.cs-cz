---
title: -pdb (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: dc7ea6aae6aa429efdf1a2dca23a3d679cb21fb7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526578"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (možnosti kompilátoru C#)
**- Pdb** – možnost kompilátoru Určuje název a umístění souboru pro symboly ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název a umístění souboru pro symboly ladění.  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte [-debug (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilátor vytvoří soubor .pdb ve stejném adresáři, ve kterém kompilátor vytvoří výstupní soubor (.exe nebo .dll) s názvem souboru, který je stejný jako název výstupního souboru.  
  
 **-pdb** vám umožní určit jiné než výchozí název a umístění souboru pdb.  
  
 Tato možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio ani ji není možné změnit prostřednictvím kódu programu.  
  
## <a name="example"></a>Příklad  
 Kompilace `t.cs` a vytvoření souboru .pdb s názvem tt.pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
