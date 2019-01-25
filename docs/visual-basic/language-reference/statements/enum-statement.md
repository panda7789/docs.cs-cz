---
title: Enum – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: f1086fdc26f1909e751617b78e0cd31f2a8b1b95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656658"
---
# <a name="enum-statement-visual-basic"></a>Enum – příkaz (Visual Basic)
Deklaruje výčet a definuje hodnoty jeho členů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>Součásti  
  
-   `attributelist`  
  
     Volitelné. Seznam atributů, které platí pro tento výčet. Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").  
  
     <xref:System.FlagsAttribute> Atribut označuje, že hodnota instance výčtu může obsahovat více členů výčtu a, že každý člen představuje bitového pole hodnoty výčtu.  
  
-   `accessmodifier`  
  
     Volitelné. Určuje, jaký kód může přistupovat k tento výčet. Může být jedna z následujících akcí:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Private Protected](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     Volitelné. Určuje, že tento výčet znovu deklaruje a skryje identicky pojmenovanou programovací prvek, nebo sadu přetížených elementů v základní třídě. Můžete zadat [stíny](../../../visual-basic/language-reference/modifiers/shadows.md) pouze na samotného výčtu, nikoli na kterýkoli z jejích členů.  
  
-   `enumerationname`  
  
     Povinný parametr. Název výčtu. Informace o platné názvy najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     Volitelné. Datový typ výčtu a všechny její členy.  
  
-   `memberlist`  
  
     Povinný parametr. Seznam členů konstanty deklarované v tomto prohlášení. Víc členů se zobrazí na jednotlivé zdrojové řádky kódu.  
  
     Každý `member` má následující syntaxi a části: `[<attribute list>] member name [ = initializer ]`  
  
    |Část|Popis|  
    |---|---|  
    |`membername`|Povinný parametr. Název tohoto člena.|  
    |`initializer`|Volitelné. Výraz, který je vyhodnocen v době kompilace a přiřazené k tomuto členu.|  
  
-   `End``Enum`  
  
     Ukončuje `Enum` bloku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud máte sadu neměnné hodnot, které logicky vzájemně souvisí, můžete je definovat společně ve výčtu. To umožňuje smysluplné názvy výčtu a její členy, které jsou jednodušší mějte na paměti než jejich hodnoty. Pak můžete použít členy výčtu na mnoha místech ve vašem kódu.  
  
 Mezi výhody používání výčtů, patří:  
  
-   Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.  
  
-   Umožňuje snadno ke změně hodnot v budoucnu.  
  
-   Díky kód lépe čitelný, což znamená, že je méně pravděpodobné, že budou zavedeny chyby.  
  
-   Zajišťuje kompatibilitu. Pokud používáte výčty, váš kód je méně pravděpodobné, že selhat, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.  
  
 Výčet má název, příslušný datový typ a sadu členů. Každý člen představuje konstantu.  
  
 Výčet deklarována třída, struktura, modul nebo rozhraní úroveň mimo všechny procedury, je *člen výčtu*. Je členem třídy, struktury, modul nebo rozhraní, které se deklaruje.  
  
 Výčty člen je přístupný z kdekoli v rámci třídy, struktury, modul nebo rozhraní. Kód mimo třídu, strukturu nebo modul musí kvalifikovat název člena výčtu s názvem této třídy, struktury nebo modulu. Vyhnete nutnosti použití plně kvalifikovaných názvů tak, že přidáte [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) příkaz ke zdrojovému souboru.  
  
 Výčet deklarován na úrovni oboru názvů, mimo třídu, strukturu, modul nebo rozhraní, je členem oboru názvů, ve kterém se zobrazí.  
  
 *Kontext deklarace* pro výčet musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedurou. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Můžete použít atributy k vyčíslení jako celek, ale ne k jeho členy jednotlivě. Atribut přispívá informací o metadatech sestavení.  
  
## <a name="data-type"></a>Datový typ  
 `Enum` Příkazu můžete deklarovat datový typ výčtu. Každý člen má datový typ výčtu. Můžete zadat `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, nebo `UShort`.  
  
 Pokud nezadáte `datatype` pro výčet, každý člen má datový typ jeho `initializer`. Pokud zadáte obě `datatype` a `initializer`, datový typ `initializer` musí být převeditelný na `datatype`. Pokud ani `datatype` ani `initializer` je k dispozici, výchozí hodnota je typu dat `Integer`.  
  
## <a name="initializing-members"></a>Inicializace členů  
 `Enum` Příkazu můžete inicializovat obsah vybrané členy v `memberlist`. Použijete `initializer` zadat výraz, který má být přiřazena k členu.  
  
 Pokud nezadáte `initializer` pro člena, Visual Basic inicializuje ji buď na hodnotu nula (Pokud je první `member` v `memberlist`), nebo na hodnotu větší než bezprostředně před jednou `member`.  
  
 Výraz zadaný v každém `initializer` může být libovolná kombinace literály, jiné konstanty, které jsou již definovány a členy výčtu, které jsou již definovány, včetně předchozí členů tohoto výčtu. Aritmetické a logické operátory můžete kombinovat takovýchto prvků.  
  
 Nelze použít proměnné nebo funkce v `initializer`. Ale můžete použít klíčová slova převodu například `CByte` a `CShort`. Můžete také použít `AscW` při volání s konstantou `String` nebo `Char` argument, protože, který může být vyhodnocen v době kompilace.  
  
 Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou. Pokud člen je přiřazena hodnota s plovoucí desetinnou čárkou a `Option Strict` nastavená na on, dojde k chybě kompilátoru. Pokud `Option Strict` je vypnuté, hodnota je automaticky převedena na `Enum` typu.  
  
 Pokud hodnotu členu překračuje povolený rozsah pro příslušný datový typ, nebo pokud je inicializovat kteréhokoli člena na maximální hodnotu povolenou příslušný datový typ, kompilátor nahlásí chybu.  
  
## <a name="modifiers"></a>Modifikátory  
 Třída, struktura, modul a rozhraní člen výčty výchozí veřejný přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu. Namespace člen výčty výchozí přístup typu friend. Můžete nastavit jejich úrovně veřejnosti, ale ne k soukromé nebo chráněné. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Všechny členy výčtu mít veřejný přístup a žádné modifikátory přístupu nelze použít na ně. Ale pokud stejný jako daný výčet má omezenější úroveň přístupu, úroveň přístupu zadaný výčet má přednost.  
  
 Ve výchozím nastavení všechny výčty jsou typy a jejich polí jsou konstanty. Proto `Shared`, `Static`, a `ReadOnly` klíčová slova nelze použít při deklaraci výčtu ani jejích členů.  
  
## <a name="assigning-multiple-values"></a>Přiřazení více hodnot  
 Výčty obvykle představují vzájemně se vylučuje hodnoty. Zahrnutím <xref:System.FlagsAttribute> atribut `Enum` prohlášení, můžete místo toho přiřadit víc hodnot do instance výčtu. <xref:System.FlagsAttribute> Atribut určuje, že výčet považovány za bitové pole, to znamená, že sada příznaků. Toto nastavení se nazývá *bitový* výčty.  
  
 Pokud deklarujete výčet pomocí <xref:System.FlagsAttribute> atribut, doporučujeme použít mocninu 2, který je 1, 2, 4, 8, 16 a tak dále, pro hodnoty. Doporučujeme také, že "None" být jméno člena, jehož hodnota je 0. Další pokyny najdete v části <xref:System.FlagsAttribute> a <xref:System.Enum>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `Enum` příkazu. Všimněte si, že člen se označuje jako `EggSizeEnum.Medium`a ne jako `Medium`.  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Metoda v následujícím příkladu je mimo `Egg` třídy. Proto `EggSizeEnum` je plně kvalifikovaný jako `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Enum` příkaz k definování související sadu s názvem konstantní hodnoty. V tomto případě hodnoty jsou barvy, které můžete se rozhodnout pro návrh formulářů pro zadávání dat pro databázi.  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje hodnoty, které obsahují kladná a záporná čísla.  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `As` klauzule slouží k určení `datatype` výčtu.  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít bitový výčtu. Víc hodnot je přiřadit k instanci bitové operace výčtu. `Enum` Deklarace obsahuje <xref:System.FlagsAttribute> atribut, který označuje, že výčtu lze považovat za sada příznaků.  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad provede iteraci výčet. Používá <xref:System.Enum.GetNames%2A> metody k načtení pole názvy členů výčtu, a <xref:System.Enum.GetValues%2A> k načtení pole hodnoty členů.  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konstanty a výčty](../../../visual-basic/language-reference/constants-and-enumerations.md)
