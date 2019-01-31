---
title: Hodnotu typu '<typename1>' nelze převést na typ '<typename2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: cd2f6e4b51bc327826301d3c7b39c97a4bed3793
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261240"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>Hodnotu typu '\<NázevTypu1 >' nelze převést na "\<NázevTypu2 >"
Hodnotu typu '\<NázevTypu1 >' nelze převést na "\<NázevTypu2 >'. Neshody typů může být způsobena kombinováním odkazu na soubor s odkazem na projekt do sestavení '\<assemblyname >'. Nahraďte odkaz na soubor "\<filepath >' v projektu"\<projectname1 >' s odkazem na projekt '\<projectname2 >'.  
  
 V situaci, kdy projekt vytvoří odkaz na projekt a odkaz na soubor kompilátor zaručit, že jeden typ lze převést na jiný.  
  
 Následující kód pseudo ukazuje situaci, která mohou generovat k této chybě.  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Projekt `P1` vytváří odkaz nepřímý projektu prostřednictvím projektu `P2` do projektu `P3`a také přímý odkaz na soubor na `P3`. Deklarace `commonObject` používá odkaz na soubor `P3`, při volání `P2.getCommonClass` používá odkaz na projekt do `P3`.  
  
 Problém v této situaci je, že odkaz na soubor Určuje název výstupního souboru a cesta k souboru `P3` (obvykle p3.dll), zatímco odkazy projektu identifikovat zdrojový projekt (`P3`) podle názvu projektu. Z tohoto důvodu nelze kompilátor zaručit, že typ `P3.commonClass` pochází ze stejného zdrojového kódu přes dvě různé odkazy.  
  
 Tuto situaci obvykle dochází, když projekt odkazy a odkazy na soubory jsou smíšené. V předchozí ilustraci by problém nastat, pokud `P1` provedené přímý odkaz na `P3` namísto odkazu na soubor.  
  
 **ID chyby:** BC30955  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Změňte odkaz na soubor odkazu na projekt.  
  
## <a name="see-also"></a>Viz také:
- [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)

