---
title: "Hodnota typu č. 39; &lt;NázevTypu1&gt;& č. 39; nelze převést na & č. 39;&lt; NázevTypu2&gt;& č. 39; (Více odkazů na soubor)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords: BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc6138c7a7ca7d50a56fdd1f536e8d2dc3462a08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Hodnota typu č. 39; &lt;NázevTypu1&gt;& č. 39; nelze převést na & č. 39;&lt; NázevTypu2&gt;& č. 39; (Více odkazů na soubor)
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
 [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
