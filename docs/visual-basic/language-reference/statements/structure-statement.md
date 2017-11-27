---
title: "Structure – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43211bb10793acf3bfe0c1d7a35791114170ee7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="structure-statement"></a>Structure – příkaz
Deklaruje název strukturu a představuje definici proměnné, vlastností, události a postupy, které tvoří strukturu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attributelist`|Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Volitelné. Označuje částečné definice struktury. V tématu [částečné](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Požadováno. Název této struktury. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že toto je obecná struktura.|  
|`typelist`|Vyžaduje, pokud použijete [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo. Seznam parametrů typu pro tuto strukturu. V tématu [zadejte seznam](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Volitelné. Označuje, že tato struktura implementuje členy jedno nebo více rozhraní. V tématu [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Vyžaduje, pokud použijete `Implements` příkaz. Názvy rozhraní, které implementuje tuto strukturu.|  
|`datamemberdeclarations`|Požadováno. Nula nebo více `Const`, `Dim`, `Enum`, nebo `Event` příkazy deklarace *datové členy* struktury.|  
|`methodmemberdeclarations`|Volitelné. Nula nebo více deklarací z `Function`, `Operator`, `Property`, nebo `Sub` postupů, které slouží jako *metoda členy* struktury.|  
|`End Structure`|Požadováno. Ukončí `Structure` definice.|  
  
## <a name="remarks"></a>Poznámky  
 `Structure` Příkaz definuje typ složeného hodnoty, kterou si můžete přizpůsobit. A *struktura* je generalizaci uživatelem definovaný typ (UDT) předchozích verzí aplikace Visual Basic. Další informace najdete v tématu [struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Struktury podporují řadu stejných funkcí jako třídy. Například struktury mohou mít vlastnosti a postupy, že můžete implementovat rozhraní a můžete používat parametrizované konstruktory. Existují však významné rozdíly mezi struktury a třídy v oblasti, například dědičnosti, deklarace a používání. Také jsou odkazové typy třídy a struktury jsou typy hodnot. Další informace najdete v tématu [struktury a třídy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Můžete použít `Structure` pouze na úrovni oboru názvů nebo modul. To znamená *deklarace kontextu* struktury musí být zdrojový soubor, obor názvů, třídy, struktury, modul nebo rozhraní a nemůže být procedura nebo bloku. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Struktury jako výchozí [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Vnoření.** Můžete definovat jeden struktury v rámci jiného. Vnější struktura, se nazývá *obsahující strukturu*, se nazývá vnitřní struktura *vnořené struktury*. Členové vnořené struktury nelze však přistupovat prostřednictvím strukturu obsahující. Místo toho je třeba deklarovat proměnnou vnořené strukturu datového typu.  
  
-   **Deklarace členů.** Každý člen struktury, musí deklarovat. Struktura člen nemůže být [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) nebo `Protected Friend` protože nic může dědit vlastnosti z struktury. Struktura samostatně, ale může být `Protected` nebo `Protected Friend`.  
  
     Je možné deklarovat v počtu nula či více sdíleném proměnné nebo sdíleném, nevlastní události ve struktuře. I když některé z nich jsou sdíleném nemůže mít pouze konstanty, vlastnosti a postupů.  
  
-   **Inicializace.** Nelze inicializovat hodnota kteréhokoli člena sdíleném datové struktury v rámci jeho deklaraci. Inicializace dat člena prostřednictvím parametrizované konstruktor na strukturu nebo po vytvoření instance struktury přiřadit hodnotu člena.  
  
-   **Dědičnost.** Struktury nemůže Zdědit z libovolného typu jiné než <xref:System.ValueType>, ze které dědí všechny struktury. Konkrétně jeden struktura nemůže Zdědit z jiné.  
  
     Nelze použít [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md) v definici struktura i k určení <xref:System.ValueType>.  
  
-   **Implementace.** Pokud používá strukturu [Implements – příkaz](../../../visual-basic/language-reference/statements/implements-statement.md), je nutné implementovat každý člen definované každé rozhraní, zadejte v `interfacenames`.  
  
-   **Výchozí vlastnost.** Struktury můžete zadat maximálně jednu vlastnost jako jeho *výchozí vlastnost*pomocí [výchozí](../../../visual-basic/language-reference/modifiers/default.md) modifikátor. Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** V rámci struktury můžou deklarovat každého člena s vlastní úrovně přístupu. Všechny členové struktury výchozí [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup. Všimněte si, že pokud strukturu samotné má omezenější úroveň přístupu, to automaticky brání přístupu k její členy i v případě, že požadovanou úroveň přístupu s modifikátory přístupu.  
  
-   **Rozsah.** Struktura je v oboru v celé jeho obsahující obor názvů, třídy, struktury nebo modulu.  
  
     Rozsah všech členů struktury je celá struktura.  
  
-   **Doba platnosti.** Struktury sám nemá životnost. Místo toho každá instance této struktury má životnost nezávislé na všechny ostatní instance.  
  
     Doba platnosti instance začíná, když je vytvořené [operátor New](../../../visual-basic/language-reference/operators/new-operator.md) klauzule. Ukončí ho při životnost proměnné, která obsahuje ukončení.  
  
     Doba platnosti struktura instance nelze rozšířit. Modul zajišťuje sblížení k funkcím statické struktury. Další informace najdete v tématu [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Členové struktury mají v závislosti na tom, jak a kde jsou deklarovány životnosti. Další informace najdete v tématu "Doba trvání" v [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Kvalifikace.** Kód mimo strukturu, musíte před jméno člena s názvem této struktury.  
  
     Pokud kód uvnitř vnořené struktury vytváří nekvalifikované odkaz na element programování, Visual Basic vyhledá pro element nejprve vnořené struktury, pak v jeho obsahující strukturu, a tak dále nejkrajnější obsahující element. Další informace najdete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Využití paměti.** Stejně jako u všech složené datové typy, nelze počítat bezpečně celkové paměti spotřeby strukturou společně přidáním přidělení nominální úložiště svých členů. Kromě toho nelze předpokládat bezpečně, že pořadí úložiště v paměti je stejný jako vaši objednávku deklarace. Pokud potřebujete k řízení rozložení úložiště struktury, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut `Structure` příkaz.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Structure` příkaz k definování sady souvisejících dat pro zaměstnance. Ukazuje použití `Public`, `Friend`, a `Private` členy tak, aby odrážela citlivosti datové položky. Také ukazuje postup, vlastnosti a události členy.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Třídy a struktury](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
