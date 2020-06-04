---
title: <message> Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt pro sestavení '<assemblyname>'.
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 263e30f992ef58b0053acb2fd749d0d9186ef6b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397256"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<message> Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt pro sestavení '\<assemblyname>'.
\<message>Tato chyba může být také způsobena kombinováním odkazu na soubor s odkazem na projekt na sestavení \<assemblyname> . V takovém případě nahraďte odkaz na soubor \<assemblyfilename> v projektu ' \<projectname1> ' s odkazem na projekt ' \<projectname2> '.  
  
 Kód v projektu přistupuje ke členu jiného projektu, ale konfigurace vašeho řešení neumožňuje kompilátoru Visual Basic vyřešit odkaz.  
  
 Pro přístup k typu definovanému v jiném sestavení musí mít kompilátor Visual Basic odkaz na toto sestavení. Musí se jednat o jediný nejednoznačný odkaz, který nezpůsobuje cyklické odkazy mezi projekty.  
  
 **ID chyby:** BC30971  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Určete, který projekt vytváří nejlepší sestavení pro váš projekt k referenci. Pro toto rozhodnutí můžete použít kritéria, jako je například snadné přístupu k souborům a četnost aktualizací.  
  
2. Ve vlastnostech projektu přidejte odkaz na projekt, který obsahuje sestavení definující typ, který používáte.  
  
## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
- [Odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Řešení potíží s poškozenými odkazy](/visualstudio/ide/troubleshooting-broken-references)
