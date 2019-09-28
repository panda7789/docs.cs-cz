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
ms.openlocfilehash: acfe47f52ede289093b3554a7dd190ef3f0e2c80
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592114"
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
|`attrlist`|Volitelný parametr. Seznam atributů, které se vztahují na tento typ. [Seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) je nutné uzavřít do lomených závorek (`< >`).|  
|`accessmodifier`|Volitelný parametr. Určuje, jaký kód má k tomuto typu přístup. Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelný parametr. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Volitelný parametr. Viz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Volitelný parametr. Viz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Povinný parametr. Název tohoto typu Musí odpovídat názvu definovanému ve všech ostatních částečných deklaracích stejného typu.|  
|`Of`|Volitelný parametr. Určuje, že se jedná o obecný typ. Viz [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Vyžaduje [se, pokud používáte.](../../../visual-basic/language-reference/statements/of-clause.md) Viz [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelný parametr. Viz [příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Vyžaduje se, pokud používáte `Inherits`. Název třídy nebo rozhraní, ze kterého je tato třída odvozena.|  
|`Implements`|Volitelný parametr. Viz [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Vyžaduje se, pokud používáte `Implements`. Názvy rozhraní, které tento typ implementuje.|  
|`variabledeclarations`|Volitelný parametr. Příkazy, které deklarují další proměnné a události pro daný typ.|  
|`proceduredeclarations`|Volitelný parametr. Příkazy, které deklarují a definují další postupy pro typ.|  
|`End Class` Nebo `End Structure`|Ukončí tuto částečnou definici `Class` nebo `Structure`.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic používá definice částečné třídy pro oddělení vygenerovaného kódu od uživatelem vytvořeného kódu v samostatných zdrojových souborech. Například **Návrhář formuláře Windows** definuje částečné třídy pro ovládací prvky, jako je například <xref:System.Windows.Forms.Form>. V těchto ovládacích prvcích byste neměli upravovat generovaný kód.  
  
 Všechna pravidla pro třídu, strukturu, rozhraní a vytváření modulů, jako jsou například pro použití modifikátoru a dědičnosti, se použijí při vytváření částečného typu.  
  
## <a name="best-practices"></a>Doporučené postupy  
  
- Za běžných okolností byste neměli rozdělit vývoj jednoho typu ve dvou nebo více deklaracích. Ve většině případů proto nepotřebujete klíčové slovo `Partial`.  
  
- Z důvodu čitelnosti by měla každá částečná deklarace typu zahrnovat klíčové slovo `Partial`. Kompilátor umožňuje nejvýše jednu částečnou deklaraci, aby klíčové slovo bylo vynecháno. Pokud je vynecháte dva nebo více, kompilátor signalizuje chybu.  
  
## <a name="behavior"></a>Chování  
  
- **Sjednocení deklarací.** Kompilátor považuje typ za sjednocení všech jeho částečných deklarací. Všechny modifikátory od každé částečné definice platí pro celý typ a každý člen z každé částečné definice je k dispozici pro celý typ.  
  
- **Pro částečné typy v modulech není povolena propagace typu.** Pokud je v modulu Částečná definice, typ propagace tohoto typu je automaticky připraven. V takovém případě může sada částečných definic způsobit neočekávané výsledky a dokonce i chyby kompilátoru. Další informace najdete v tématu o [typu propagace](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Kompilátor sloučí částečné definice pouze v případě, že jsou jejich plně kvalifikované cesty identické.  
  
 Klíčové slovo `Partial` lze použít v těchto kontextech:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je rozdělena definice třídy `sampleClass` do dvou deklarací, z nichž každá definuje jinou proceduru `Sub`.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Dvě částečné definice v předchozím příkladu můžou být ve stejném zdrojovém souboru nebo ve dvou různých zdrojových souborech.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
