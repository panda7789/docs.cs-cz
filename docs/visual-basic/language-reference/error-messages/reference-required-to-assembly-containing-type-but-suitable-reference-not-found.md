---
title: Odkaz vyžadoval sestavení '<assemblyidentity>' obsahující typ '<typename>'. Nebylo však možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty '<projectname1>' a '<projectname2>'.
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 4b9f74f0627268752b0ba3c3816fe9d4cc8a231b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404820"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>Odkaz vyžadoval sestavení '\<assemblyidentity>' obsahující typ '\<typename>'. Nebylo však možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty '\<projectname1>' a '\<projectname2>'.
Výraz používá typ, jako je třída, struktura, rozhraní, výčet nebo delegát, které jsou definovány mimo váš projekt. Nicméně máte odkazy na projekt na více než jedno sestavení, které definuje tento typ.  
  
 Citované projekty vytváří sestavení se stejným názvem. Proto kompilátor nemůže určit, které sestavení se má použít pro typ, ke kterému přistupujete.  
  
 Pro přístup k typu definovanému v jiném sestavení musí mít kompilátor Visual Basic odkaz na toto sestavení. Musí se jednat o jediný nejednoznačný odkaz, který nezpůsobuje cyklické odkazy mezi projekty.  
  
 **ID chyby:** BC30969  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Určete, který projekt vytváří nejlepší sestavení pro váš projekt k referenci. Pro toto rozhodnutí můžete použít kritéria, jako je například snadné přístupu k souborům a četnost aktualizací.  
  
2. Ve vlastnostech projektu přidejte odkaz na soubor, který obsahuje sestavení definující typ, který používáte.  
  
## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
- [Odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Řešení potíží s poškozenými odkazy](/visualstudio/ide/troubleshooting-broken-references)
