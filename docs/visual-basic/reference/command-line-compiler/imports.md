---
title: -Imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 929e24a1ffd02d4e21ab1b925ddd59050b5d3cc4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005572"
---
# <a name="-imports-visual-basic"></a>-Imports (Visual Basic)
Importuje obory názvů z určeného sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`namespaceList`|Požadováno. Seznam oborů názvů oddělených čárkami, které se mají importovat|  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-imports` importuje libovolný obor názvů definovaný v aktuální sadě zdrojových souborů nebo z libovolného odkazovaného sestavení.  
  
 Členy v oboru názvů zadané s `-imports` jsou k dispozici pro všechny soubory zdrojového kódu v kompilaci. Použijte [příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k použití oboru názvů v jednom souboru zdrojového kódu.  
  
|Nastavení/Imports v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **odkazy** .<br />3. Zadejte název oboru názvů do pole vedle tlačítka **Přidat import uživatele** .<br />4. klikněte na tlačítko **Přidat import uživatele** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje, pokud je zadána hodnota `/imports:system.globalization`. Bez této akce kompilace vyžaduje, aby příkaz `Imports System.Globalization` byl zahrnut na začátku souboru zdrojového kódu nebo aby byla vlastnost plně kvalifikovaná jako `System.Globalization.CultureInfo.CurrentCulture.Name`.

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
