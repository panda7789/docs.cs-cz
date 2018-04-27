---
title: Deklarované názvy elementu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad883dd8e1de419c74b5bcdb8762994e762b4cf7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="declared-element-names-visual-basic"></a>Deklarované názvy elementu (Visual Basic)
Každý element, deklarované má název, označované taky jako *identifikátor*, což je kód používá na ni odkazuje.  
  
## <a name="rules"></a>Pravidla  
 Název elementu v jazyce Visual Basic musí odpovídat následujícím pravidlům:  
  
-   Musí začínat znakem abecedy nebo podtržítkem (`_`).  
  
-   Musí obsahovat pouze znaky abecedy, číslice desítkové soustavy a podtržítka.  
  
-   Musí obsahovat alespoň jeden znak abecedy nebo číslici desítkové soustavy Pokud začíná podtržítkem.  
  
-   Nesmí být víc než 1023 znaků.  
  
 Maximální délku 1023 znaků platí také pro celý řetězec plně kvalifikovaný název, například `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 Následující příklad ukazuje některé názvy platný element.  
  
 `aB123__45`  
  
 `_567`  
  
 Následující příklad ukazuje některé názvy neplatný element. První pouze podtržítko, druhý začíná desítková číslice a třetí obsahuje neplatný znak ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Názvy elementů začíná podtržítkem (`_`) jsou nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md) CLS (), takže kompatibilní se specifikací CLS kód nelze použít komponenty, která definuje takové názvy. Podtržítkem v každém místě v název elementu je však kompatibilní se specifikací CLS.  
  
### <a name="name-length-guidelines"></a>Název délka pokyny  
 Prakticky musí být název co nejkratší při identifikaci stále jasně povaha elementu. Tím zlepšuje čitelnost kódu a snižuje velikost řádku délku a zdrojový soubor.  
  
 Název nesmí být na druhé straně krátké tak, že nepopisuje adekvátní element reprezentuje a jak ji používá váš kód. To je důležité pro čitelnost kódu. Pokud někdo jiný pokouší porozumět, nebo pokud sami hledáte na to dlouhou dobu, po ho napsal, můžete uložit názvy vhodný elementu značné množství času.  
  
## <a name="escaped-names"></a>Řídicí názvy  
 Název elementu obecně nesmí odpovídat některé z klíčových slov rezervován jazyka Visual Basic, jako například `Case` nebo `Friend`. Však můžete definovat *uvozené název*, který je do hranatých závorek (`[ ]`). Uvozený název může odpovídat všechny klíčové slovo jazyka Visual Basic, vzhledem k tomu, že hranatých závorkách odebrat všechny nejednoznačnosti. Můžete také hranaté závorky odkazovat na název později v kódu.  
  
 Obecně platí, měli byste použít řídicí názvy pouze tehdy, když:  
  
-   Váš kód migroval z předchozí verze jazyka Visual Basic, který není rezervovat – klíčové slovo používá jako název; nebo  
  
-   Pracujete s kódem v jiném jazyce, ve kterém není vyhrazena daným klíčovým slovem.  
  
 Jinak byste měli zvážit, přejmenování elementu, pokud jeho název je v konfliktu s klíčovým slovem. Integrované vývojové prostředí (IDE) poskytuje snadný způsob, jak to udělat. Další informace najdete v tématu [Refactoring](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Malá a velká písmena v názvech  
 Názvy elementů v jazyce Visual Basic jsou velká a malá písmena. To znamená, že když kompilátor porovná dva názvy, které se liší v abecedním případě pouze, je je interpretuje jako se stejným názvem. Například považuje `ABC` a `abc` odkazovat na stejný element deklarovaný.  
  
 Modul CLR (CLR) ale používá vazba malá a velká písmena. Proto při vytváření sestavení nebo knihovny DLL a zpřístupněte ho ostatních sestavení, názvy již nejsou velká a malá písmena. Například, pokud definice třídy s prvek s názvem `ABC`, a ujistěte se, ostatních sestavení pomocí vaší třídy prostřednictvím modul common language runtime, musí odkazovat na prvek jako `ABC`. Pokud následně znovu zkompiluje třídě a změňte název elementu `abc`, ostatních sestavení pomocí vlastní třídy již přístup tohoto prvku. Proto při uvolnění aktualizovanou verzi sestavení byste neměli měnit abecedním malá jakýchkoli veřejných složek.  
  
## <a name="names-and-locales"></a>Názvy a národní prostředí  
 Porovnávání názvů je nezávislé na národním prostředí. Pokud se dva názvy shodují v jedné národního prostředí, jsou zaručit tak, aby odpovídaly ve všech národních prostředí.  
  
## <a name="see-also"></a>Viz také  
 [Deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
