---
title: Hodnotu typu '<typename1>' nelze převést na '<typename2>' (odkazy na více souborů).
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 7371cbd4fef4abced95744071ff222b40e160e3e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620311"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>Hodnotu typu '\<NázevTypu1 >' nelze převést na "\<NázevTypu2 >' (odkazy na více souborů)
Hodnotu typu '\<NázevTypu1 >' nelze převést na "\<NázevTypu2 >'. Neshody typů může být způsobena kombinováním odkazu na soubor "\<filepath1 >' v projektu"\<projectname1 >' s odkazem na soubor "\<filepath2 >' v projektu"\<projectname2 >'. Pokud jsou obě sestavení identická, zkuste, nahraďte tyto odkazy tak, aby oba odkazy byly ze stejného umístění.  
  
 V situaci, kdy projekt vytvoří více než jeden soubor odkaz na sestavení kompilátor zaručit, že jeden typ lze převést na jiný.  
  
 Každý odkaz na soubor Určuje název výstupního souboru projektu (obvykle souboru knihovny DLL) a cesta k souboru. Kompilátor nemůže zaručit, že výstupní soubory pocházejí ze stejného zdroje, nebo že představují stejné verze téhož sestavení. Proto nemůže zaručit, že typy v jiné odkazy jsou stejného typu nebo ještě, že jedna může být převeden na druhý.  
  
 Pokud víte, že odkazovaná sestavení mají stejnou identitu sestavení, můžete použít odkaz na jeden soubor. *Identita sestavení* obsahuje název sestavení, verze, veřejného klíče, pokud existuje a jazykové verze. Tyto informace jednoznačně identifikuje sestavení.  
  
 **ID chyby:** BC30961  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud odkazovaná sestavení mají stejnou identitu sestavení, odebrat nebo nahradit jeden z odkazů na soubory tak, aby se pouze odkaz na jeden soubor.  
  
- Pokud odkazovaná sestavení nemají stejnou identitu sestavení, pak změňte kód tak, aby se nebude pokoušet o převod typu v jednom typu v jiném.  
  
## <a name="see-also"></a>Viz také:

- [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
