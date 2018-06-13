---
title: Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt; &#39; (více odkazů na soubor)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603688"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt; &#39; (více odkazů na soubor)
Hodnotu typu '\<NázevTypu1 >' nelze převést na '\<NázevTypu2 > ". Neshoda typu může být z důvodu kombinování odkazu na soubor '\<filepath1 >' v projektu '\<projectname1 >' s odkazem na soubor '\<filepath2 >' v projektu '\<projectname2 > ". Pokud jsou obě sestavení identická, zkuste vyměnit tyto odkazy tak, aby byly oba odkazy ze stejného umístění.  
  
 V situaci, kdy projektu umožňuje více než jeden soubor odkaz na sestavení kompilátor nezaručuje, že jeden typ lze převést na jiný.  
  
 Každý odkaz na soubor Určuje název výstupního souboru projektu (obvykle soubor knihovny DLL) a cesta k souboru. Kompilátor nemůže zaručit, že výstupní soubory pocházejí z jednoho zdroje, nebo že představují stejnou verzi nástroje do stejného sestavení. Proto nemůže zaručit, že typy v různých odkazy jsou stejného typu nebo i než lze převést na druhý.  
  
 Pokud víte, že jsou odkazovaná sestavení mít stejnou identitu sestavení můžete použít jeden soubor odkaz. *Identity sestavení* obsahuje název, verzi, veřejný klíč, pokud existuje a jazykovou verzi sestavení. Tyto informace jednoznačně identifikuje sestavení.  
  
 **ID chyby:** BC30961  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud jsou odkazovaná sestavení mít stejnou identitu sestavení, odeberte nebo nahraďte jeden z odkazů na soubor tak, aby bylo pouze odkaz na jeden soubor.  
  
-   Pokud odkazovaná sestavení nemají stejnou identitu sestavení, pak změňte kód tak, aby se nebude pokoušet o převést na typ v jeden typ v dalších.  
  
## <a name="see-also"></a>Viz také  
 [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)  
 
