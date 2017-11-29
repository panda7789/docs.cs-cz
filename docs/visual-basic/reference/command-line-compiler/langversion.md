---
title: /langversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfe91588471cc8410b25addea8d66a0388c9c5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-visual-basic"></a>/langversion (Visual Basic)
Způsobí, že kompilátor tak, aby přijímal pouze syntaxi, která je součástí zadaná verze jazyka Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Požadováno. Jazyková verze, která mají být použity během kompilace. Platné hodnoty jsou `9`, `9.0`, `10`, a `10.0`.  
  
## <a name="remarks"></a>Poznámky  
 `/langversion` Možnost určuje, jaké syntaxe kompilátor přijímá. Například pokud jste určili, zda je verze jazyka 9.0, kompilátor generuje chyby syntaxe, která je platná pouze ve verzi 10.0 a novější.  
  
 Tuto možnost můžete použít při vývoji aplikací tento cíl různé verze rozhraní .NET Framework. Například pokud cílíte na rozhraní .NET Framework 3.5, můžete použít tuto možnost k zajištění nepoužívejte syntaxe z jazyková verze 10.0.  
  
 Můžete nastavit `/langversion` přímo jen pomocí příkazového řádku. Další informace najdete v tématu [cílení na konkrétní verzi rozhraní .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `sample.vb` pro 9.0 Visual Basic.  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Cílení na konkrétní rozhraní .NET Framework verze](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
