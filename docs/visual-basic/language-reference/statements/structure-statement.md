---
title: Structure – příkaz (Visual Basic)
ms.date: 05/12/2018
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
ms.openlocfilehash: 9377d889f56049720ab10439582300913f5cbb37
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44065729"
---
# <a name="structure-statement"></a>Structure – příkaz
Deklaruje název struktury a zavádí definici proměnných, vlastností, událostí a postupů, které tvoří strukturu.  
  
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
|`attributelist`|Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [chráněný](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend –](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Chráněné typu Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Privátní, chráněné](../../language-reference/modifiers/private-protected.md) <br /><br /> Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Volitelné. Označuje částečnou definici struktury. Zobrazit [částečné](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Požadováno. Název této struktury. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že se jedná o obecnou strukturu.|  
|`typelist`|Povinné, pokud používáte [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo. Seznam parametrů typu v této struktuře. Zobrazit [seznamu](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Volitelné. Označuje, že tato struktura implementuje členy jednoho nebo více rozhraní. Zobrazit [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Povinné, pokud používáte `Implements` příkazu. Názvy rozhraní, které implementuje tato struktura.|  
|`datamemberdeclarations`|Požadováno. Nula nebo více `Const`, `Dim`, `Enum`, nebo `Event` příkazy deklarace *datové členy* struktury.|  
|`methodmemberdeclarations`|Volitelné. Nula nebo více deklarací `Function`, `Operator`, `Property`, nebo `Sub` postupy, které slouží jako *členové metody* struktury.|  
|`End Structure`|Požadováno. Ukončuje `Structure` definice.|  
  
## <a name="remarks"></a>Poznámky  
 `Structure` Prohlášení definuje složený typ hodnoty, kterou můžete přizpůsobit. A *struktura* je generalizace uživatelem definovaného typu (UDT) z předchozích verzí jazyka Visual Basic. Další informace najdete v tématu [struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Struktury podporují mnoho stejných funkcí jako třídy. Například struktury mohou mít vlastnosti a postupy, mohou implementovat rozhraní a mohou mít parametrizované konstruktory. Nicméně existují významné rozdíly mezi strukturami a třídami v oblastech, jako je dědičnost, prohlášení a využití. Také třídy jsou odkazové typy a struktury jsou typy hodnot. Další informace najdete v tématu [struktury a třídy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Můžete použít `Structure` pouze na úrovni oboru názvů nebo modulu. To znamená, že *kontext deklarace* pro strukturu musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nesmí být procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Struktury výchozí pro [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>pravidla  
  
-   **Vnoření.** Můžete definovat jednu strukturu v jiné. Vnější struktura se nazývá *obsahující struktura*, a vnitřní struktura se nazývá *vnořené struktury*. K členům vnořené konstrukce však nelze přistupovat prostřednictvím obsažené struktury. Místo toho je třeba deklarovat proměnnou datového typu vnořené struktury.  
  
-   **Deklarace člena.** Je třeba deklarovat každého člena struktury. Člen struktury nemůže být [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) nebo `Protected Friend` protože nic zdědit ze struktury. Struktura samotná však může být `Protected` nebo `Protected Friend`.  
  
     Můžete deklarovat nula nebo více nesdílených proměnných nebo nesdílených, nevlastních událostí ve struktuře. Nemůžete mít pouze konstanty, vlastnosti a postupy, i když jsou některé z nich nesdílené.  
  
-   **Inicializace.** Nelze inicializovat hodnotu žádného nesdíleného datového člena struktury jako součást její deklarace. Musíte inicializovat takového datového člena parametrizovaným konstruktorem ve struktuře nebo přiřadit hodnotu člena po vytvoření instance struktury.  
  
-   **Dědičnost.** Struktura nemůže dědit z libovolného typu jiného než <xref:System.ValueType>, ze kterého dědí všechny struktury. Zejména jedna struktura nemůže dědit z jiné.  
  
     Nelze použít [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md) v definici struktury, ani k určení <xref:System.ValueType>.  
  
-   **Implementace.** Pokud struktura používá [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md), musíte implementovat každého člena definovaného každým rozhraním, zadejte v `interfacenames`.  
  
-   **Výchozí vlastnost.** Struktura může určit nejvýše jednu vlastnost jako jeho *výchozí vlastnost*, použije [výchozí](../../../visual-basic/language-reference/modifiers/default.md) modifikátor. Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** V rámci struktury můžete deklarovat každého člena se svou vlastní úroveň přístupu. Všechny členy struktury přejdou ve výchozím nastavení [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup. Všimněte si, že pokud má sama struktura omezenější úroveň přístupu, automaticky to omezuje přístup k jejím členům, i v případě, že upravíte jejich úroveň přístupu modifikátory přístupu.  
  
-   **Obor.** Struktura je v oboru v celém jeho nadřazeného oboru názvů, třídy, struktury nebo modulu.  
  
     Obor každého člena struktury je celá struktura.  
  
-   **Doba platnosti.** Struktura sama nemá životnost. Místo toho každá instance této struktury má životnost nezávislou na všech ostatních instancích.  
  
     Životnost instance začne, když je vytvořena [operátor New](../../../visual-basic/language-reference/operators/new-operator.md) klauzuli. Končí při ukončení platnosti proměnné, která obsahuje skončí.  
  
     Nelze prodloužit životnost instance struktury. Modul zajišťuje aproximaci funkce statické struktury. Další informace najdete v tématu [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Členové struktury mají životnost v závislosti na tom, jak a kde jsou deklarovány. Další informace najdete v tématu "Životnost" [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Kvalifikace.** Kód mimo strukturu musí kvalifikovat název člena s názvem této struktury.  
  
     Pokud kód uvnitř vnořené struktury vytváří nekvalifikovaný odkaz na programovací prvek, Visual Basic vyhledá prvek nejprve ve vnořené struktuře, pak v jeho obsahující struktuře, a tak dále navýšení kapacity na vnější obsahující element. Další informace najdete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Využití paměti.** Stejně jako u všech složených datových typů nelze bezpečně vypočítat celkovou spotřebu paměti struktury sečtením nominálních přidělení úložiště jejích členů. Kromě toho nelze bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí prohlášení. Pokud potřebujete řídit rozložení úložiště struktury, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut `Structure` příkazu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Structure` příkaz k definování sady souvisejících dat pro zaměstnance. Ukazuje použití `Public`, `Friend`, a `Private` členy pro vyznačení citlivosti datových položek. Také ukazuje proceduru, vlastnost a členy události.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Struktury a třídy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
