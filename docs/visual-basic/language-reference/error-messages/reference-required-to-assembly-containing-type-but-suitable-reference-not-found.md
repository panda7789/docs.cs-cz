---
title: "Odkaz vyžadoval sestavení & č. 39; &lt;assemblyidentity&gt;& č. 39; obsahující typ & č. 39;&lt; TypeName&gt;& č. 39; ale nebyl nalezen vhodný odkaz z důvodu nejednoznačnosti mezi projekty & č. 39;&lt; projectname1&gt;& č. 39; a & č. 39;&lt; projectname2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ca2454f5c306b3defd1c885dfd59ee130f3e828
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Odkaz vyžadoval sestavení & č. 39; &lt;assemblyidentity&gt;& č. 39; obsahující typ & č. 39;&lt; TypeName&gt;& č. 39; ale nebyl nalezen vhodný odkaz z důvodu nejednoznačnosti mezi projekty & č. 39;&lt; projectname1&gt;& č. 39; a & č. 39;&lt; projectname2&gt;& č. 39;
Výraz používá typu, například třída, struktura, rozhraní, výčet nebo delegáta, který je definován mimo projekt. Máte ale odkazy na projekt k definování typu více než jednom sestavení.  
  
 Citovaný projekty vytvořit sestavení se stejným názvem. Kompilátor proto nemůže určit sestavení, které použije pro typ přistupují.  
  
 Pro přístup k typu definovaný v jiném sestavení, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru musí mít odkaz na tohoto sestavení. Toto musí být jeden jednoznačným odkaz, který nevyvolá Kruhové odkazy mezi projekty.  
  
 **ID chyby:** BC30969  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určete, které projektu vytvoří doporučené sestavení pro svůj projekt tak, aby odkazovaly. Pro toto rozhodnutí můžete použít kritérií, například snadný přístup k souborům a četnost aktualizací.  
  
2.  Ve vlastnostech projektu přidejte odkaz na soubor, který obsahuje sestavení, která definuje typ, který používáte.  
  
## <a name="see-also"></a>Viz také  
 [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [Řešení potíží s poškozenými odkazy](/visualstudio/ide/troubleshooting-broken-references)
