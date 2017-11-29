---
title: Partial (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5129ef7737b1b07317d47f8d18e9aceb668bf05a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
|`End Class`nebo`End Structure`|Ukončí toto částečné `Class` nebo `Structure` definice.|  
  
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
  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad rozdělí definice třídy `sampleClass` do dvou deklarace, z nichž každý definuje jiné `Sub` postupu.  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 Dva částečné definice v předchozím příkladu může být ve stejném souboru zdroje nebo ve dvou různých zdrojové soubory.  
  
## <a name="see-also"></a>Viz také  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [Stínů](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
