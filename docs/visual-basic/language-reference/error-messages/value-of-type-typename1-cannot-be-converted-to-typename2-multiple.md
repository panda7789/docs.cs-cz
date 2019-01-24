---
title: Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt; &#39; (odkazy na více souborů)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 943b9612a9217b90c19f34285e812c4e1cccf81a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691370"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt; &#39; (odkazy na více souborů)
Hodnotu typu '\<NázevTypu1 >' nelze převést na "\<NázevTypu2 >'. Neshody typů může být způsobena kombinováním odkazu na soubor "\<filepath1 >' v projektu"\<projectname1 >' s odkazem na soubor "\<filepath2 >' v projektu"\<projectname2 >'. Pokud jsou obě sestavení identická, zkuste, nahraďte tyto odkazy tak, aby oba odkazy byly ze stejného umístění.  
  
 V situaci, kdy projekt vytvoří více než jeden soubor odkaz na sestavení kompilátor zaručit, že jeden typ lze převést na jiný.  
  
 Každý odkaz na soubor Určuje název výstupního souboru projektu (obvykle souboru knihovny DLL) a cesta k souboru. Kompilátor nemůže zaručit, že výstupní soubory pocházejí ze stejného zdroje, nebo že představují stejné verze téhož sestavení. Proto nemůže zaručit, že typy v jiné odkazy jsou stejného typu nebo ještě, že jedna může být převeden na druhý.  
  
 Pokud víte, že odkazovaná sestavení mají stejnou identitu sestavení, můžete použít odkaz na jeden soubor. *Identita sestavení* obsahuje název sestavení, verze, veřejného klíče, pokud existuje a jazykové verze. Tyto informace jednoznačně identifikuje sestavení.  
  
 **ID chyby:** BC30961  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud odkazovaná sestavení mají stejnou identitu sestavení, odebrat nebo nahradit jeden z odkazů na soubory tak, aby se pouze odkaz na jeden soubor.  
  
-   Pokud odkazovaná sestavení nemají stejnou identitu sestavení, pak změňte kód tak, aby se nebude pokoušet o převod typu v jednom typu v jiném.  
  
## <a name="see-also"></a>Viz také:
- [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)

