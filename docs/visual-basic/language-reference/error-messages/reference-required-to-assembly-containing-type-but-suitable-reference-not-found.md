---
title: Odkaz vyžadoval sestavení &#39; &lt;assemblyidentity&gt; &#39; obsahující typ &#39; &lt;typename&gt;&#39;, ale nebylo možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty &#39; &lt;projectname1&gt; &#39; a &#39; &lt;projectname2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 1a0c2a2fd235026729901153a0c0c300f914a78f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553006"
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Odkaz vyžadoval sestavení &#39; &lt;assemblyidentity&gt; &#39; obsahující typ &#39; &lt;typename&gt;&#39;, ale nebylo možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty &#39; &lt;projectname1&gt; &#39; a &#39; &lt;projectname2&gt;&#39;
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
