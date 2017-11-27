---
title: "&lt;zpráva&gt; této chyby mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení & č. 39;&lt; AssemblyName&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30e5d5aca09e7b74e16dd05cdc0c5c361c1657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;zpráva&gt; této chyby mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení & č. 39;&lt; AssemblyName&gt;& č. 39;
\<Zpráva > tuto chybu mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení '\<assemblyname >. V takovém případě zkuste vyměnit odkaz na soubor '\<assemblyfilename >' v projektu '\<projectname1 >' s odkaz na projekt se\<projectname2 > ".  
  
 Kód ve vašem projektu přistupuje členem jiného projektu, ale neumožňuje konfiguraci vašeho řešení [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru odkaz na řešení.  
  
 Pro přístup k typu definovaný v jiném sestavení, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru musí mít odkaz na tohoto sestavení. Toto musí být jeden jednoznačným odkaz, který nevyvolá Kruhové odkazy mezi projekty.  
  
 **ID chyby:** BC30971  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určete, které projektu vytvoří doporučené sestavení pro svůj projekt tak, aby odkazovaly. Pro toto rozhodnutí můžete použít kritérií, například snadný přístup k souborům a četnost aktualizací.  
  
2.  Ve vlastnostech projektu přidejte odkaz na projekt, který obsahuje sestavení, která definuje typ, který používáte.  
  
## <a name="see-also"></a>Viz také  
 [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [Řešení potíží s poškozenými odkazy](/visualstudio/ide/troubleshooting-broken-references)
