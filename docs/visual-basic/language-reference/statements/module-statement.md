---
title: "Module – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92cdcd1919f21243118108da3bc382ea5d954130
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="module-statement"></a>Module – příkaz
Deklaruje název modulu a představuje definici proměnné, vlastností, události a postupy, které se skládá z modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Volitelné. Může být jedna z následujících akcí:  
  
-   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Požadováno. Název tohoto modulu. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `statements`  
 Volitelné. Příkazy, které definují proměnné, vlastnosti, události, postupy a vnořené typy tohoto modulu.  
  
 `End Module`  
 Ukončí `Module` definice.  
  
## <a name="remarks"></a>Poznámky  
 A `Module` definuje příkaz k dispozici v rámci svého oboru názvů odkazového typu. A *modulu* (někdy nazývané *standardní modulu*) je podobný na třídu, ale některé důležité rozdíly. Každý modul se přesně jedna instance a není nutné vytvořit či přiřazený k proměnné. Moduly nepodporují dědičnosti nebo implementovat rozhraní. Všimněte si, že modul není *typ* v tom smyslu, že třídu nebo strukturu – nelze deklarovat jako programovací element mít datový typ modulu.  
  
 Můžete použít `Module` jenom na úrovni oboru názvů. To znamená *deklarace kontextu* pro modul musí být zdrojový soubor nebo obor názvů a nemůže být třída, struktura, modulu, rozhraní, postup nebo bloku. Nelze vnořit modul v rámci jiný modul, nebo libovolného typu. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Modul má stejnou dobu života jako programu. Vzhledem k tomu, že jsou všechny její členy `Shared`, mají také životnosti rovnající se tohoto programu.  
  
 Moduly výchozí [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Implicitně se všichni její členové modulu `Shared`.  
  
## <a name="classes-and-modules"></a>Třídy a modulů  
 Tyto prvky mít mnoho podobností, ale existuje několik důležitých rozdílů.  
  
-   **Terminologie.** Předchozí verze jazyka Visual Basic rozpoznat dva typy modulů: *třídy modulů* (.cls soubory) a *standardní moduly* (BAS soubory). Aktuální verze volá tyto *třídy* a *moduly*, v uvedeném pořadí.  
  
-   **Sdílení členové.** Můžete určit, zda je sdílenou člena třídy nebo instance člena.  
  
-   **Objekt orientace.** Třídy jsou objektově orientované, ale nejsou moduly. Proto pouze třídy se dá vytvořit instance jako objekty. Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Modifikátory.** Všichni členové modulu jsou implicitně [sdílené](../../../visual-basic/language-reference/modifiers/shared.md). Nelze použít `Shared` – klíčové slovo deklarace členem a nelze změnit sdílený stav kteréhokoli člena.  
  
-   **Dědičnost.** Modul nemůže Zdědit z libovolného typu, jiné než <xref:System.Object>, ze které všechny moduly dědí. Konkrétně jeden modul nemůže Zdědit z jiné.  
  
     Nelze použít [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md) v definici modulu i k určení <xref:System.Object>.  
  
-   **Výchozí vlastnost.** V modulu nelze definovat všechny výchozí vlastnosti. Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** V modulu můžou deklarovat každého člena s vlastní úrovně přístupu. Výchozí modul členy [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup kromě proměnných a konstant, které používá výchozí [privátní](../../../visual-basic/language-reference/modifiers/private.md) přístup. Pokud modul má omezený přístup k více než jeden z jejích členů, úroveň přístupu zadaný modul přednost.  
  
-   **Rozsah.** Modul je v oboru v rámci svého oboru názvů.  
  
     Rozsah všech členů modulu je celý modulu. Všimněte si, že všichni členové podstoupit *zadejte povýšení*, což způsobí, že jejich obor, který má být převeden na obor názvů, který obsahuje modul. Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
-   **Kvalifikace.** Máte více modulů v projektu a můžou deklarovat členy se stejným názvem ve dvou nebo více modulů. Pokud je odkaz z mimo tento modul však musíte před všechny odkazy na člena s názvem příslušný modul. Další informace najdete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Namespace – příkaz](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
