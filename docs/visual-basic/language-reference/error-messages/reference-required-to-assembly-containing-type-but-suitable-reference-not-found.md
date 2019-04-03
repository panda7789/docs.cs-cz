---
title: Odkaz vyžadoval sestavení '<assemblyidentity>' obsahující typ '<typename>'. Nebylo však možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty '<projectname1>' a '<projectname2>'.
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 3cfdf8150c8ccd9e1b4f047cd1ce8ee4ad6bbc1a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813402"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>Odkaz vyžadoval sestavení '\<assemblyidentity >' obsahující typ "\<typename >", ale nebylo možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty\<projectname1 > "a"\< projectname2 > "
Výraz používá typ, jako jsou třídy, struktury, rozhraní, výčet nebo delegáta, který je definován vně vašeho projektu. Máte ale odkazy na více než jedno sestavení, definice typu.  
  
 Citovaný projekty vytváří sestavení se stejným názvem. Proto kompilátor nemůže určit sestavení, které použije pro typ přistupují.  
  
 Pro přístup k typ definovaný v jiném sestavení, musí mít kompilátoru jazyka Visual Basic odkazu na toto sestavení. Musí se jednat jednoznačnou, kompletní jeden odkaz, který nezpůsobí cyklické odkazy mezi projekty.  
  
 **ID chyby:** BC30969  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určete, který projekt vytvoří nejlepší sestavení pro projekt tak, aby odkazovaly. Pro toto rozhodnutí můžete použít kritéria, jako je například usnadnění přístupu k souborům a četnosti aktualizací.  
  
2.  Ve vlastnostech vašeho projektu přidejte odkaz na soubor, který obsahuje sestavení, které definuje typ, který používáte.  
  
## <a name="see-also"></a>Viz také:

- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Řešení potíží s poškozenými odkazy](/visualstudio/ide/troubleshooting-broken-references)
