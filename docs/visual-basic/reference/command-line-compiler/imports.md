---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: cc9fc222843bdfe8e49d2d291dc36ff3e0c63fc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408592"
---
# <a name="-imports-visual-basic"></a>-Imports (Visual Basic)
Importuje obory názvů z určeného sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`namespaceList`|Povinná hodnota. Seznam oborů názvů oddělených čárkami, které se mají importovat|  
  
## <a name="remarks"></a>Poznámky  
 `-imports`Možnost importuje libovolný obor názvů definovaný v aktuální sadě zdrojových souborů nebo z libovolného odkazovaného sestavení.  
  
 Členové v oboru názvů, které jsou zadány, `-imports` jsou k dispozici pro všechny soubory zdrojového kódu v kompilaci. Použijte [příkaz Imports (obor názvů a typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) k použití oboru názvů v jednom souboru zdrojového kódu.  
  
|Nastavení – importy v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **odkazy** .<br />3. Zadejte název oboru názvů do pole vedle tlačítka **Přidat import uživatele** .<br />4. klikněte na tlačítko **Přidat import uživatele** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje, pokud `-imports:system.globalization` je zadán. Bez této akce kompilace vyžaduje, aby `Imports System.Globalization` příkaz byl zahrnut na začátku souboru zdrojového kódu nebo aby byla vlastnost plně kvalifikována jako `System.Globalization.CultureInfo.CurrentCulture.Name` .

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Odkazy a příkaz Imports](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
