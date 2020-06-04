---
title: Hodnotu typu '<typename1>' nelze převést na '<typename2>' (odkazy na více souborů).
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 25008f05979638e050b74fc659fdc0a6d13b3c31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406583"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>Hodnotu typu '\<typename1>' nelze převést na '\<typename2>' (odkazy na více souborů).
Hodnotu typu \<typename1> nejde převést na \<typename2> . Neshoda typů může být způsobena kombinováním odkazu na soubor \<filepath1> v projektu \<projectname1> s odkazem na soubor \<filepath2> v projektu \<projectname2> . Pokud jsou obě sestavení identická, nahraďte tyto odkazy tak, aby oba odkazy byly ze stejného umístění.  
  
 V situaci, kdy projekt vytváří více než jeden odkaz na soubor sestavení, nemůže kompilátor zaručit, že jeden typ lze převést na jiný typ.  
  
 Každý odkaz na soubor určuje cestu k souboru a název výstupního souboru projektu (obvykle soubor DLL). Kompilátor nemůže zaručit, že výstupní soubory pocházejí ze stejného zdroje nebo že představují stejnou verzi stejného sestavení. Proto nemůže zaručit, že typy v různých odkazech jsou stejného typu nebo dokonce že jeden lze převést na druhý.  
  
 Pokud víte, že odkazovaná sestavení mají stejnou identitu sestavení, můžete použít jeden odkaz na soubor. *Identita sestavení* zahrnuje název sestavení, verzi, veřejný klíč, pokud existuje, a jazykovou verzi. Tyto informace jednoznačně identifikují sestavení.  
  
 **ID chyby:** BC30961  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud mají odkazovaná sestavení stejnou identitu sestavení, odeberte nebo nahraďte jeden z odkazů na soubory tak, aby byl pouze jeden odkaz na soubor.  
  
- Pokud odkazovaná sestavení nemají stejnou identitu sestavení, pak změňte kód tak, aby se nepokoušel převést typ v jednom na jiný typ.  
  
## <a name="see-also"></a>Viz také

- [Převody typů v jazyce Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
