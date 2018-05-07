---
title: '&lt;zpráva&gt; této chyby mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení &#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 498ca74497077e3268aa8cb25ce5121f3c9ea59d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;zpráva&gt; této chyby mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení &#39; &lt;assemblyname&gt;&#39;
\<Zpráva > tuto chybu mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení '\<assemblyname >. V takovém případě zkuste vyměnit odkaz na soubor '\<assemblyfilename >' v projektu '\<projectname1 >' s odkaz na projekt se\<projectname2 > ".  
  
 Kód ve vašem projektu přistupuje členem jiného projektu, ale konfigurace řešení neumožňuje Visual Basic – kompilátor odkaz na řešení.  
  
 Chcete-li přistupovat k typu definovaný v jiném sestavení, Visual Basic – kompilátor musí mít odkaz na sestavení. Toto musí být jeden jednoznačným odkaz, který nevyvolá Kruhové odkazy mezi projekty.  
  
 **ID chyby:** BC30971  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určete, které projektu vytvoří doporučené sestavení pro svůj projekt tak, aby odkazovaly. Pro toto rozhodnutí můžete použít kritérií, například snadný přístup k souborům a četnost aktualizací.  
  
2.  Ve vlastnostech projektu přidejte odkaz na projekt, který obsahuje sestavení, která definuje typ, který používáte.  
  
## <a name="see-also"></a>Viz také  
 [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [Řešení potíží s poškozenými odkazy](/visualstudio/ide/troubleshooting-broken-references)
