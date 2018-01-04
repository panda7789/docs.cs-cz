---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cdb7cff2221930113d6b49a640da0844f175f1b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="imports-visual-basic"></a>/imports (Visual Basic)
Obory názvů importuje ze zadaného sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`namespaceList`|Požadováno. Čárkami oddělený seznam obory názvů určených k importu.|  
  
## <a name="remarks"></a>Poznámky  
 `/imports` Možnost importuje obor názvů definované v rámci aktuální sadu zdrojových souborů nebo z všechny odkazované sestavení.  
  
 Členy v oboru názvů zadaným `/imports` jsou k dispozici pro všechny soubory zdrojového kódu v kompilace. Použít [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pomocí oboru názvů v souboru jednoho zdrojového kódu.  
  
|Chcete-li nastavit/importuje v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **odkazy** kartě.<br />3.  Zadejte název oboru názvů do pole vedle položky **přidat Import uživatelů** tlačítko.<br />4.  Klikněte **přidat Import uživatelů** tlačítko.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje při `/imports:system` je zadán.  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
