---
title: Partial (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: c94c3bf1a1e3e4c724f90690f52e97e8216cb9a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604611"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Označuje, že je typ deklarace částečnou definici typu.  
  
 Definici typu mezi několik deklarace můžete rozdělit pomocí `Partial` – klíčové slovo. Můžete vytvořit tolik částečné deklarace tak, jak chcete v tolik jiných zdrojových souborů. Všechny deklarace však musí být ve stejném sestavení a o stejný obor názvů.  
  
> [!NOTE]
>  Visual Basic podporuje *částečné metody*, které jsou obvykle implementované v částečné třídy. Další informace najdete v tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) a [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attrlist`|Volitelné. Seznam atributů, které se vztahují k tomuto typu. Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách (`< >`).|  
|`accessmodifier`|Volitelné. Určuje, jaký kód můžete přístup tohoto typu. V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Volitelné. V tématu [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Volitelné. V tématu [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Požadováno. Název tohoto typu. Musí odpovídat názvu definována v jiné částečné deklarace stejného typu.|  
|`Of`|Volitelné. Určuje, že se jedná o obecného typu. V tématu [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Vyžaduje, pokud použijete [z](../../../visual-basic/language-reference/statements/of-clause.md). V tématu [zadejte seznam](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. V tématu [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Vyžaduje, pokud použijete `Inherits`. Název třídy nebo rozhraní, ze které je tato třída odvozena.|  
|`Implements`|Volitelné. V tématu [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Vyžaduje, pokud použijete `Implements`. Názvy rozhraní, které implementuje tohoto typu.|  
|`variabledeclarations`|Volitelné. Příkazy, které deklarace další proměnné a událostí pro typ.|  
|`proceduredeclarations`|Volitelné. Příkazy, které deklarace a definice dalších kroků pro typ.|  
|`End Class` Nebo `End Structure`|Ukončí toto částečné `Class` nebo `Structure` definice.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic používá definice částečné třídy pro oddělení generovaného kódu z kódu uživatelem definovaných v samostatných zdrojové soubory. Například **Windows Form Designer** definuje částečné třídy pro ovládací prvky, jako <xref:System.Windows.Forms.Form>. Neměli upravovat generovaného kódu v těchto ovládacích prvků.  
  
 Všechna pravidla pro třídy, struktury, rozhraní a vytváření modulu, třeba kroky týkající se použití modifikátor a dědičnost, použít při vytváření typu částečné.  
  
## <a name="best-practices"></a>Doporučené postupy  
  
-   Za normálních podmínek by neměl rozdělit vývoj jednoho typu do dvou nebo více deklarace. Proto ve většině případů není třeba `Partial` – klíčové slovo.  
  
-   Čitelnější, by měly obsahovat všechny částečné deklaraci typu `Partial` – klíčové slovo. Kompilátor umožňuje maximálně jeden částečné deklarace vynechat – klíčové slovo; Pokud dva nebo více vynechejte kompilátor nevydá signál k chybě.  
  
## <a name="behavior"></a>Chování  
  
-   **Sjednocení deklarace.** Kompilátor považuje za sjednocení všech částečné deklarace typu. Každý modifikátor z každé částečné definice platí pro celý typ a každý člen z každé částečné definice je k dispozici pro celý typ.  
  
-   **Propagace typu není povoleno pro částečné typů v modulech.** Pokud definici částečné uvnitř modulu, typu povýšení tohoto typu je automaticky nepotlačí. V takovém případě sadu částečné definice může způsobit neočekávané výsledky a i chyby kompilátoru. Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Kompilátor sloučí částečné definice jenom v případě, že jsou identické jejich plně kvalifikované cesty.  
  
 `Partial` – Klíčové slovo lze použít v těchto kontexty:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad rozdělí definice třídy `sampleClass` do dvou deklarace, z nichž každý definuje jiné `Sub` postupu.  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 Dva částečné definice v předchozím příkladu může být ve stejném souboru zdroje nebo ve dvou různých zdrojové soubory.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
