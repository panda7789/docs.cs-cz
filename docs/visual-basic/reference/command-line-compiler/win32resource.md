---
title: /win32resource
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d839b1100b1ae76fbd4653ebc60c79db11b77685
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="win32resource"></a>/win32resource
Vloží zdrojového souboru Win32 ve výstupním souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název souboru prostředků pro přidání do výstupního souboru. Uzavřete název souboru v uvozovkách ("") Pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Můžete vytvořit zdrojového souboru Win32 s Microsoft Windows prostředků kompilátoru (RC).  
  
 Win32 prostředků může obsahovat verzi nebo informace o bitové mapy (ikona), která pomáhá identifikovat aplikace v **Průzkumníka souborů**. Pokud nezadáte `/win32resource`, kompilátor vygeneruje informace o verzi na základě verze sestavení. `/win32resource` a `/win32icon` možnosti se vzájemně vylučují.  
  
 Najdete v části [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkazu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků, nebo [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků.  
  
> [!NOTE]
>  `/win32resource` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí zdrojového souboru Win32 `Rf.res`:  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
