---
title: Názvy deklarovaných XML elementů a atributů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: e33d396dac8ae5f9afd057a27f27bee700092f71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634347"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Názvy deklarovaných XML elementů a atributů (Visual Basic)
Toto téma obsahuje pokyny pro Visual Basic pro vytváření názvů XML elementů a atributů v literálech XML.  V literálu XML můžete zadat místní název nebo kvalifikovaný název. Úplný název se skládá z předponu oboru názvů XML, dvojtečku a místní název. Další informace o předpon názvového prostoru XML, naleznete v tématu [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>pravidla  
 Místní název elementu nebo atributu v jazyce Visual Basic musí splňovat následující pravidla.  
  
-   Můžete začít s oborem názvů. Musí začínat znakem abecedy nebo podtržítkem (`_`).  
  
-   Musí obsahovat jenom abecední znaky, desítkové číslice, podtržítka, tečky (.) a pomlčky (-).  
  
-   Nesmí být více než 1024 znaků.  
  
-   Použití dvojteček, které se zobrazují v názvech označení vymezení oboru názvů. Proto můžete pomocí dvojtečky pouze k určení obor názvů XML pro konkrétní název.  
  
 Kromě toho by měl splňovat následujícími pravidly.  
  
-   Specifikace XML 1.0 si vyhrazuje všechna jména začíná tímto řetězcem "xml" jakékoliv změny malá a velká písmena. Proto nepoužívejte tyto názvy pro prvek a atributů.  
  
### <a name="name-length-guidelines"></a>Pokyny pro délka názvu  
 Prakticky, název by měl být co nejkratší při identifikaci zjevně povaze elementu. To zlepšuje čitelnost vašeho kódu a zmenší velikost řádku délku a zdrojový soubor.  
  
 Vaše jméno však by neměl být tak krátký, nezabývá se odpovídajícím způsobem elementu nebo jak se váš kód používá. To je důležité pro čitelnost kódu. Pokud někdo jiný se snaží ho chápat, nebo pokud chcete sami se na něj dlouhou dobu, po ho napsal, odpovídající prvek názvy můžete ušetřit čas.  
  
## <a name="case-sensitivity-in-names"></a>Rozlišování velikosti písmen v názvech  
 Názvy elementů XML jsou malá a velká písmena. To znamená, že když kompilátor jazyka Visual Basic porovná dva názvy, které se liší abecedním pouze velikostí písmen, to je interpretuje jako odlišné názvy. Například interpretuje `ABC` a `abc` jako odkazující na jednotlivé prvky.  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 Při vytváření XML element literal, můžete zadat předponu oboru názvů XML pro název elementu. Další informace najdete v tématu [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Viz také:
- [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
