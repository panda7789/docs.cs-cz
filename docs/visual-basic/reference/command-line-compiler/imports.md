---
title: -imports (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d81e9d2bd55e6e38e337805b950a0b85680d129b
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-imports-visual-basic"></a>-imports (Visual Basic)
Obory názvů importuje ze zadaného sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`namespaceList`|Požadováno. Čárkami oddělený seznam obory názvů určených k importu.|  
  
## <a name="remarks"></a>Poznámky  
 `-imports` Možnost importuje obor názvů definované v rámci aktuální sadu zdrojových souborů nebo z všechny odkazované sestavení.  
  
 Členy v oboru názvů zadaným `-imports` jsou k dispozici pro všechny soubory zdrojového kódu v kompilace. Použít [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pomocí oboru názvů v souboru jednoho zdrojového kódu.  
  
|Chcete-li nastavit/importuje v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **odkazy** kartě.<br />3.  Zadejte název oboru názvů do pole vedle položky **přidat Import uživatelů** tlačítko.<br />4.  Klikněte **přidat Import uživatelů** tlačítko.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje při `/imports:system.globalization` je zadán. Bez toho úspěšné kompilace vyžaduje buď `Imports System.Globalization` příkaz být zahrnuté na začátku souboru se zdrojovým kódem, nebo vlastnost být plně kvalifikovaný jako `System.Globalization.CultureInfo.CurrentCulture.Name`. 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
