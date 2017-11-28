---
title: /moduleassemblyname
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9a5307970ac745b4f102d0008e64b985c00e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname"></a>/moduleassemblyname
Určuje název sestavení, které tento modul bude součástí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`assembly_name`|Název sestavení, které tento modul bude součástí.|  
  
## <a name="remarks"></a>Poznámky  
 Procesy kompilátoru `/moduleassemblyname` možnost jenom Pokud `/target:module` byla zadána možnost. To způsobí, že kompilátor Vytvořte modul. Modul vytvořené kompilátor je platná pouze pro sestavení zadaným `/moduleassemblyname` možnost. Pokud jste modul v jiném sestavení, dojde k chybám běhu.  
  
 `/moduleassemblyname` Možnost je nutný pouze v případě, že jsou pravdivé následující výroky:  
  
-   Datový typ v modulu potřebuje přístup k `Friend` typu v odkazované sestavení.  
  
-   Odkazované sestavení udělil přístup přátelských sestavení do sestavení, do které budou vytvořeny v modulu.  
  
 Další informace o vytváření modulu najdete v tématu [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Další informace o přátelských sestavení najdete v tématu [přátelských sestavení](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
> [!NOTE]
>  `/moduleassemblyname` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici, pouze při sestavování z příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytváření vícesouborového sestavení](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/ main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [/ addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [Sestavení a globální mezipaměti sestavení](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Přátelská sestavení](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
