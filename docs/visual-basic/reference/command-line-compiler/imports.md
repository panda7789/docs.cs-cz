---
title: -imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 9e5adcce85c4ca4863d28784a7d7f61c441a06c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588441"
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
|`namespaceList`|Povinný parametr. Čárkami oddělený seznam oborů názvů, které se mají naimportovat.|  
  
## <a name="remarks"></a>Poznámky  
 `-imports` Možnost importuje libovolný obor názvů definovaných v rámci aktuální sadu zdrojových souborů nebo ze všech odkazovaných sestavení.  
  
 Členové v oboru názvů zadaným `-imports` jsou k dispozici pro všechny soubory zdrojového kódu dané kompilace. Použít [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro použití oboru názvů v souboru jednoho zdrojového kódu.  
  
|Chcete-li nastavit/importuje v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **odkazy** kartu.<br />3.  Zadejte název oboru názvů v seznamu vedle možnosti **přidat Import uživatelů** tlačítko.<br />4.  Klikněte na tlačítko **přidat Import uživatelů** tlačítko.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje, kdy `/imports:system.globalization` je zadán. Bez něho úspěšné kompilace vyžaduje buď `Imports System.Globalization` příkazem být zahrnuty na začátku souboru se zdrojovým kódem, nebo jako plně kvalifikovat vlastnost `System.Globalization.CultureInfo.CurrentCulture.Name`. 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
