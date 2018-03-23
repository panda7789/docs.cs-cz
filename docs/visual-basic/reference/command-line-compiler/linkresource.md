---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b84631e0c09521a6f4ff9e06b2a80e0885862e
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Vytvoří odkaz na spravovaných prostředků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Požadováno. Soubor prostředků pro odkaz na sestavení. Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách ("").  
  
 `identifier`  
 Volitelné. Logický název prostředku. Název, který se používá k načtení prostředku. Výchozí hodnota je název souboru. Volitelně můžete zadat, zda se soubor nachází veřejných nebo privátních v manifestu sestavení, například: `-linkres:filename.res,myname.res,public`. Ve výchozím nastavení `filename` je veřejný v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 `-linkresource` Možnost nevloží souboru prostředků ve výstupním souboru, pomocí `-resource` možnost to udělat.  
  
 `-linkresource` Možnost vyžaduje jednu z `-target` možnosti jiné než `-target:module`.  
  
 Pokud `filename` je [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků vytvořili, například pomocí [Resgen.exe (Generátor zdrojových souborů)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) nebo ve vývojovém prostředí k němu se členy v <xref:System.Resources> oboru názvů. (Další informace najdete v tématu <xref:System.Resources.ResourceManager>.) Pro přístup k jiným prostředkům v době běhu, použít metody, které začínají `GetManifestResource` v <xref:System.Reflection.Assembly> třídy.  
  
 Název souboru může být jakékoli formát souboru. Například můžete chtít nativní knihovny DLL součástí sestavení, ujistěte se, aby mohli být nainstalován do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.  
  
 Zkratka pro `-linkresource` je `-linkres`.  
  
> [!NOTE]
>  `-linkresource` Možnost není k dispozici z vývojovém prostředí sady Visual Studio, je k dispozici, pouze při sestavování z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `in.vb` a odkazy na soubor prostředků `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
