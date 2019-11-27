---
title: Částečně
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
ms.openlocfilehash: df85571b757fd54496677bad1195fab9690b79cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351361"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Označuje, že deklarace typu je částečná definice typu.  
  
 Definici typu můžete rozdělit mezi několik deklarací pomocí klíčového slova `Partial`. Můžete použít libovolný počet částečných deklarací v libovolných různých zdrojových souborech, kolik chcete. Nicméně všechny deklarace musí být ve stejném sestavení a stejném oboru názvů.  
  
> [!NOTE]
> Visual Basic podporuje *částečné metody*, které jsou obvykle implementovány v dílčích třídách. Další informace naleznete v tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) a [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
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
|`attrlist`|Volitelná. Seznam atributů, které se vztahují na tento typ. [Seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) je nutné uzavřít do lomených závorek (`< >`).|  
|`accessmodifier`|Volitelná. Určuje, jaký kód má k tomuto typu přístup. Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelná. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Volitelná. Viz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Volitelná. Viz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Požadováno. Název tohoto typu Musí odpovídat názvu definovanému ve všech ostatních částečných deklaracích stejného typu.|  
|`Of`|Volitelná. Určuje, že se jedná o obecný typ. Viz [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Vyžaduje [se, pokud používáte.](../../../visual-basic/language-reference/statements/of-clause.md) Viz [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelná. Viz [příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Vyžaduje se, pokud používáte `Inherits`. Název třídy nebo rozhraní, ze kterého je tato třída odvozena.|  
|`Implements`|Volitelná. Viz [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Vyžaduje se, pokud používáte `Implements`. Názvy rozhraní, které tento typ implementuje.|  
|`variabledeclarations`|Volitelná. Příkazy, které deklarují další proměnné a události pro daný typ.|  
|`proceduredeclarations`|Volitelná. Příkazy, které deklarují a definují další postupy pro typ.|  
|`End Class` nebo `End Structure`|Ukončí tuto částečnou `Class` nebo definici `Structure`.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic používá definice částečné třídy pro oddělení vygenerovaného kódu od uživatelem vytvořeného kódu v samostatných zdrojových souborech. Například **Návrhář formuláře Windows** definuje částečné třídy pro ovládací prvky, jako je například <xref:System.Windows.Forms.Form>. V těchto ovládacích prvcích byste neměli upravovat generovaný kód.  
  
 Všechna pravidla pro třídu, strukturu, rozhraní a vytváření modulů, jako jsou například pro použití modifikátoru a dědičnosti, se použijí při vytváření částečného typu.  
  
## <a name="best-practices"></a>Doporučené postupy  
  
- Za běžných okolností byste neměli rozdělit vývoj jednoho typu ve dvou nebo více deklaracích. Proto ve většině případů nepotřebujete klíčové slovo `Partial`.  
  
- Pro účely čitelnosti by měla každá částečná deklarace typu zahrnovat klíčové slovo `Partial`. Kompilátor umožňuje nejvýše jednu částečnou deklaraci, aby klíčové slovo bylo vynecháno. Pokud je vynecháte dva nebo více, kompilátor signalizuje chybu.  
  
## <a name="behavior"></a>Chování  
  
- **Sjednocení deklarací.** Kompilátor považuje typ za sjednocení všech jeho částečných deklarací. Všechny modifikátory od každé částečné definice platí pro celý typ a každý člen z každé částečné definice je k dispozici pro celý typ.  
  
- **Pro částečné typy v modulech není povolena propagace typu.** Pokud je v modulu Částečná definice, typ propagace tohoto typu je automaticky připraven. V takovém případě může sada částečných definic způsobit neočekávané výsledky a dokonce i chyby kompilátoru. Další informace najdete v tématu o [typu propagace](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Kompilátor sloučí částečné definice pouze v případě, že jsou jejich plně kvalifikované cesty identické.  
  
 Klíčové slovo `Partial` lze použít v těchto kontextech:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je rozdělena definice třídy `sampleClass` do dvou deklarací, z nichž každá definuje jiný způsob `Sub`.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Dvě částečné definice v předchozím příkladu můžou být ve stejném zdrojovém souboru nebo ve dvou různých zdrojových souborech.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
