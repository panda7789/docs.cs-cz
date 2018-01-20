---
title: "-pdb (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7528283765c2b6f4a9d5e84015526a95938a6281
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
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
