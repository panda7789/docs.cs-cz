---
title: Částečné
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
ms.openlocfilehash: 650ead2f0deb9813b26241a6a4676907de3f263d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362239"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Označuje, že deklarace typu je částečná definice typu.  
  
 Definici typu můžete rozdělit mezi několik deklarací pomocí `Partial` klíčového slova. Můžete použít libovolný počet částečných deklarací v libovolných různých zdrojových souborech, kolik chcete. Nicméně všechny deklarace musí být ve stejném sestavení a stejném oboru názvů.  
  
> [!NOTE]
> Visual Basic podporuje *částečné metody*, které jsou obvykle implementovány v dílčích třídách. Další informace naleznete v tématu [částečné metody](../../programming-guide/language-features/procedures/partial-methods.md) a [Sub Statement](../statements/sub-statement.md).  
  
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
  
|Pojem|Definice|  
|---|---|  
|`attrlist`|Nepovinný parametr. Seznam atributů, které se vztahují na tento typ. [Seznam atributů](../statements/attribute-list.md) musíte uzavřít do lomených závorek ( `< >` ).|  
|`accessmodifier`|Nepovinný parametr. Určuje, jaký kód má k tomuto typu přístup. Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Nepovinný parametr. Viz [Shadows](shadows.md).|  
|`MustInherit`|Nepovinný parametr. Viz [MustInherit](mustinherit.md).|  
|`NotInheritable`|Nepovinný parametr. Viz [NotInheritable](notinheritable.md).|  
|`name`|Povinná hodnota. Název tohoto typu Musí odpovídat názvu definovanému ve všech ostatních částečných deklaracích stejného typu.|  
|`Of`|Nepovinný parametr. Určuje, že se jedná o obecný typ. Viz [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Vyžaduje [se, pokud používáte.](../statements/of-clause.md) Viz [seznam typů](../statements/type-list.md).|  
|`Inherits`|Nepovinný parametr. Viz [příkaz Inherits](../statements/inherits-statement.md).|  
|`classname`|Vyžaduje se, pokud používáte `Inherits` . Název třídy nebo rozhraní, ze kterého je tato třída odvozena.|  
|`Implements`|Nepovinný parametr. Viz [příkaz Implements](../statements/implements-statement.md).|  
|`interfacenames`|Vyžaduje se, pokud používáte `Implements` . Názvy rozhraní, které tento typ implementuje.|  
|`variabledeclarations`|Nepovinný parametr. Příkazy, které deklarují další proměnné a události pro daný typ.|  
|`proceduredeclarations`|Nepovinný parametr. Příkazy, které deklarují a definují další postupy pro typ.|  
|`End Class` nebo `End Structure`|Ukončí tento částečný `Class` nebo `Structure` definice.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic používá definice částečné třídy pro oddělení vygenerovaného kódu od uživatelem vytvořeného kódu v samostatných zdrojových souborech. Například **Návrhář formuláře Windows** definuje částečné třídy pro ovládací prvky, jako například <xref:System.Windows.Forms.Form> . V těchto ovládacích prvcích byste neměli upravovat generovaný kód.  
  
 Všechna pravidla pro třídu, strukturu, rozhraní a vytváření modulů, jako jsou například pro použití modifikátoru a dědičnosti, se použijí při vytváření částečného typu.  
  
## <a name="best-practices"></a>Osvědčené postupy  
  
- Za běžných okolností byste neměli rozdělit vývoj jednoho typu ve dvou nebo více deklaracích. Ve většině případů proto klíčové slovo nepotřebujete `Partial` .  
  
- Z důvodu čitelnosti by měla každá částečná deklarace typu zahrnovat `Partial` klíčové slovo. Kompilátor umožňuje nejvýše jednu částečnou deklaraci, aby klíčové slovo bylo vynecháno. Pokud je vynecháte dva nebo více, kompilátor signalizuje chybu.  
  
## <a name="behavior"></a>Chování  
  
- **Sjednocení deklarací.** Kompilátor považuje typ za sjednocení všech jeho částečných deklarací. Všechny modifikátory od každé částečné definice platí pro celý typ a každý člen z každé částečné definice je k dispozici pro celý typ.  
  
- **Pro částečné typy v modulech není povolena propagace typu.** Pokud je v modulu Částečná definice, typ propagace tohoto typu je automaticky připraven. V takovém případě může sada částečných definic způsobit neočekávané výsledky a dokonce i chyby kompilátoru. Další informace najdete v tématu o [typu propagace](../../programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Kompilátor sloučí částečné definice pouze v případě, že jsou jejich plně kvalifikované cesty identické.  
  
 `Partial`Klíčové slovo lze použít v těchto kontextech:  
  
 [Class – příkaz](../statements/class-statement.md)  
  
 [Structure – příkaz](../statements/structure-statement.md)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je rozdělena definice třídy `sampleClass` do dvou deklarací, z nichž každá definuje jiný `Sub` postup.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Dvě částečné definice v předchozím příkladu můžou být ve stejném zdrojovém souboru nebo ve dvou různých zdrojových souborech.  
  
## <a name="see-also"></a>Viz také

- [Class – příkaz](../statements/class-statement.md)
- [Structure – příkaz](../statements/structure-statement.md)
- [Propagace typu](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](shadows.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Částečné metody](../../programming-guide/language-features/procedures/partial-methods.md)
