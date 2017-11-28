---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a>/linkresource (Visual Basic)
Vytvoří odkaz na spravovaných prostředků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Požadováno. Soubor prostředků pro odkaz na sestavení. Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách ("").  
  
 `identifier`  
 Volitelné. Logický název prostředku. Název, který se používá k načtení prostředku. Výchozí hodnota je název souboru. Volitelně můžete zadat, zda se soubor nachází veřejných nebo privátních v manifestu sestavení, například: `/linkres:filename.res,myname.res,public`. Ve výchozím nastavení `filename` je veřejný v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 `/linkresource` Možnost nevloží souboru prostředků ve výstupním souboru, pomocí `/resource` možnost to udělat.  
  
 `/linkresource` Možnost vyžaduje jednu z `/target` možnosti jiné než `/target:module`.  
  
 Pokud `filename` je [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků vytvořili, například pomocí [Resgen.exe (Generátor zdrojových souborů)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) nebo ve vývojovém prostředí k němu se členy v <xref:System.Resources> oboru názvů. (Další informace najdete v tématu <xref:System.Resources.ResourceManager>.) Pro přístup k jiným prostředkům v době běhu, použít metody, které začínají `GetManifestResource` v <xref:System.Reflection.Assembly> třídy.  
  
 Název souboru může být jakékoli formát souboru. Například můžete chtít nativní knihovny DLL součástí sestavení, ujistěte se, aby mohli být nainstalován do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.  
  
 Zkratka pro `/linkresource` je `/linkres`.  
  
> [!NOTE]
>  `/linkresource` Možnost není k dispozici z vývojovém prostředí sady Visual Studio, je k dispozici, pouze při sestavování z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a odkazy na soubor prostředků `Rf.resource`.  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/ Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
