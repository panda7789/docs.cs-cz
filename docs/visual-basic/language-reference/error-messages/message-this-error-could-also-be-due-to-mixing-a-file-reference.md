---
title: <message> Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt do sestavení '<assemblyname>.
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 951f90a9209ff31896f4426ceb75f05b012897a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921014"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<Zpráva > Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt do sestavení '\<assemblyname >!
\<Zpráva > Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt do sestavení '\<assemblyname >. V takovém případě zkuste vyměnit odkaz na soubor "\<assemblyfilename >' v projektu"\<projectname1 >' s odkazem na projekt '\<projectname2 >'.  
  
 Kód ve vašem projektu přistupuje k členem jiného projektu, ale konfigurace řešení není povoleno kompilátor jazyka Visual Basic přeložit odkaz.  
  
 Pro přístup k typ definovaný v jiném sestavení, musí mít kompilátoru jazyka Visual Basic odkazu na toto sestavení. Musí se jednat jednoznačnou, kompletní jeden odkaz, který nezpůsobí cyklické odkazy mezi projekty.  
  
 **ID chyby:** BC30971  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Určete, který projekt vytvoří nejlepší sestavení pro projekt tak, aby odkazovaly. Pro toto rozhodnutí můžete použít kritéria, jako je například usnadnění přístupu k souborům a četnosti aktualizací.  
  
2. Ve vlastnostech vašeho projektu přidejte odkaz na projekt, který obsahuje sestavení, které definuje typ, který používáte.  
  
## <a name="see-also"></a>Viz také:

- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Řešení potíží s poškozenými odkazy](/visualstudio/ide/troubleshooting-broken-references)
