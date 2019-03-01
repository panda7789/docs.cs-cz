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
ms.openlocfilehash: e1464421866ee22f27f9cf0a3611bc09a631c004
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975833"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Označuje, že deklarace typu je částečnou definici typu.  
  
 Definice typu mezi několik deklarací můžete rozdělit pomocí `Partial` – klíčové slovo. Můžete použít tolik částečné deklarace chcete v tolika jiných zdrojových souborů. Všechny deklarace však musí být ve stejném sestavení a stejný obor názvů.  
  
> [!NOTE]
>  Visual Basic podporuje *částečné metody*, které jsou zpravidla implementovaní v částečné třídy. Další informace najdete v tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) a [příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
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
|`accessmodifier`|Volitelné. Určuje, jaký kód může přistupovat k tohoto typu. Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Volitelné. Zobrazit [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Volitelné. Zobrazit [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Povinný parametr. Název tohoto typu. Musí odpovídat názvu definovaný v jiné částečné deklarace stejného typu.|  
|`Of`|Volitelné. Určuje, že se jedná o obecného typu. Zobrazit [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Povinné, pokud používáte [z](../../../visual-basic/language-reference/statements/of-clause.md). Zobrazit [seznamu](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. Zobrazit [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Povinné, pokud používáte `Inherits`. Název třídy nebo rozhraní, ze kterého tato třída je odvozena.|  
|`Implements`|Volitelné. Zobrazit [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Povinné, pokud používáte `Implements`. Názvy, které tento typ implementuje rozhraní.|  
|`variabledeclarations`|Volitelné. Příkazy, které deklarace události pro typ a další proměnné.|  
|`proceduredeclarations`|Volitelné. Příkazy, které deklarace a definovat další postupy pro typ.|  
|`End Class` Nebo `End Structure`|Končí tento částečné `Class` nebo `Structure` definice.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic používá definicí částečné třídy pro oddělení generovaný kód z kódu uživatelem definovaných v samostatných zdrojové soubory. Například **Návrhář formulářů Windows** definuje částečné třídy pro ovládací prvky, jako <xref:System.Windows.Forms.Form>. Generovaný kód v těchto ovládacích prvků byste neměli měnit.  
  
 Všechna pravidla pro třídu, strukturu, rozhraní a vytváření modulu, třeba kroky týkající se použití modifikátoru a dědičnost, použít při vytváření částečného typu.  
  
## <a name="best-practices"></a>Doporučené postupy  
  
-   Za normálních podmínek by neměl vývoj jeden typ rozdělit mezi dva nebo více deklarací. Proto se ve většině případů není nutné `Partial` – klíčové slovo.  
  
-   Pro lepší čitelnost, by měl obsahovat všechny částečné deklaraci typu `Partial` – klíčové slovo. Kompilátor povoluje nejvýše jedna částečná deklarace chcete vynechat, nechte – klíčové slovo; Pokud ji vynechte nejméně dva signály kompilátor chybu.  
  
## <a name="behavior"></a>Chování  
  
-   **Deklarace sjednocení.** Kompilátor zpracovává typ jako její částečné deklarace sjednocení. Každý modifikátor z každé Částečná definice platí pro celý typ a je k dispozici pro celý typ každého člena z každé částečnou definici.  
  
-   **Propagace typu není povolený pro částečné typy v modulech.** Pokud je částečnou definici uvnitř modulu, typu povýšení tohoto typu není automaticky zrušena. V takovém případě sada částečné definice může způsobit neočekávané výsledky a dokonce i chyby kompilátoru. Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Kompilátor sloučí částečné definice pouze v případě jejich úplné cesty jsou identické.  
  
 `Partial` – Klíčové slovo lze použít v těchto kontextech:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad rozdělí definice třídy `sampleClass` do dvě deklarace, z nichž každý definuje jiný `Sub` postup.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Dvě Částečná definice v předchozím příkladu může být ve stejném zdrojovém souboru nebo ve dvou různých zdrojových souborů.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
