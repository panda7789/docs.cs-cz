---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 380e71e462f736d4564a37b83567007fa9461b05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332956"
---
# <a name="-imports-visual-basic"></a>-Imports (Visual Basic)
Importuje obory názvů z určeného sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termín|Definice|  
|---|---|  
|`namespaceList`|Požadováno. Seznam oborů názvů oddělených čárkami, které se mají importovat|  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-imports` naimportuje libovolný obor názvů definovaný v aktuální sadě zdrojových souborů nebo z libovolného odkazovaného sestavení.  
  
 Členy v oboru názvů určeném pomocí `-imports` jsou k dispozici pro všechny soubory zdrojového kódu v kompilaci. Použijte [příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k použití oboru názvů v jednom souboru zdrojového kódu.  
  
|Nastavení/Imports v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **odkazy** .<br />3. Zadejte název oboru názvů do pole vedle tlačítka **Přidat import uživatele** .<br />4. klikněte na tlačítko **Přidat import uživatele** .|  
  
## <a name="example"></a>Příklad  
 Při zadání `/imports:system.globalization` je zkompilován následující kód. Bez něho, úspěšná kompilace vyžaduje, aby byl příkaz `Imports System.Globalization` zahrnut na začátku souboru zdrojového kódu nebo aby byla vlastnost plně kvalifikovaná jako `System.Globalization.CultureInfo.CurrentCulture.Name`.

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
