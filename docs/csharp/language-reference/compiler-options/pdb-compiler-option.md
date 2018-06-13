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
ms.openlocfilehash: 9f8158ec0d8de2b9249c4f69830c37480c34b390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217425"
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
 Pokud zadáte [-debug (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilátor vytvoří soubor .pdb ve stejném adresáři, kde bude vytvořen výstupní soubor (.exe nebo .dll) s názvem souboru, který je stejný jako název výstupního souboru.  
  
 **-pdb** vám umožní určit jiné než výchozí název a umístění souboru pdb.  
  
 Tato možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani ji není možné změnit prostřednictvím kódu programu.  
  
## <a name="example"></a>Příklad  
 Kompilace `t.cs` a vytvoří soubor .pdb s názvem tt.pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
