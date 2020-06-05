---
title: Hodnotu typu '<typename1>' nelze převést na typ '<typename2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: f6b35efbc445887c537b94dd299b317a28e5f689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406557"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>Hodnotu typu '\<typename1>' nelze převést na typ '\<typename2>'.
Hodnotu typu \<typename1> nejde převést na \<typename2> . Neshoda typů může být způsobena kombinováním odkazu na soubor s odkazem na projekt na sestavení ' \<assemblyname> '. Zkuste nahradit odkaz na soubor \<filepath> v projektu ' \<projectname1> ' s odkazem na projekt ' \<projectname2> '.  
  
 V situaci, kdy projekt vytvoří odkaz na projekt i odkaz na soubor, kompilátor nemůže zaručit, že jeden typ lze převést na jiný typ.  
  
 Následující pseudo kód ilustruje situaci, která může tuto chybu vygenerovat.  
  
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
  
 Projekt `P1` vytváří přímý odkaz na projekt prostřednictvím projektu `P2` do projektu `P3` a také přímý odkaz na soubor `P3` . Deklarace `commonObject` používá odkaz na soubor `P3` , zatímco volání `P2.getCommonClass` používá odkaz na projekt `P3` .  
  
 Problémem v této situaci je, že odkaz na soubor určuje cestu k souboru a název výstupního souboru `P3` (obvykle P3. dll), zatímco odkazy na projekt identifikují zdrojový projekt ( `P3` ) podle názvu projektu. Z tohoto důvodu kompilátor nemůže zaručit, že typ `P3.commonClass` pochází ze stejného zdrojového kódu prostřednictvím dvou různých odkazů.  
  
 K této situaci obvykle dochází, když jsou odkazy na projekt a odkazy na soubory smíšené. Na předchozí ilustraci se k problému nestane, pokud `P1` jste vytvořili přímý odkaz na projekt `P3` namísto odkazu na soubor.  
  
 **ID chyby:** BC30955  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Změňte odkaz na soubor na odkaz na projekt.  
  
## <a name="see-also"></a>Viz také

- [Převody typů v jazyce Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
