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
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234013"
---
# <a name="enum-statement-visual-basic"></a>Enum – příkaz (Visual Basic)
Výčet deklaruje a definuje hodnoty její členy.  
  
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
  
     <xref:System.FlagsAttribute> Atribut uvádí, že hodnota instance výčtu může obsahovat více členy výčtu a aby každý člen představuje pole bit v hodnota výčtu.  
  
-   `accessmodifier`  
  
     Volitelné. Určuje, jaký kód můžete přístup tento výčet. Může být jedna z následujících akcí:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Chráněné Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Privátní chráněný](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     Volitelné. Určuje, že tento výčet redeclares a skryje stejně jako s názvem programovací prvek, nebo sadu přetížené elementů v základní třídě. Můžete zadat [stínů](../../../visual-basic/language-reference/modifiers/shadows.md) pouze na daný výčet, nikoli na všechny její členy.  
  
-   `enumerationname`  
  
     Požadováno. Název výčtu. Informace na platné názvy najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     Volitelné. Datový typ výčtu a všechny její členy.  
  
-   `memberlist`  
  
     Požadováno. Seznam členů konstanty se deklarované v tomto příkazu. Na jednotlivé zdrojové řádky kódu se zobrazí více členů.  
  
     Každý `member` má následující syntaxe a částí: `[<attribute list>] member name [ = initializer ]`  
  
    |Část|Popis|  
    |---|---|  
    |`membername`|Požadováno. Název tohoto člena.|  
    |`initializer`|Volitelné. Výraz, který se vyhodnotí v době kompilace a přiřadí do tohoto člena.|  
  
-   `End``Enum`  
  
     Ukončí `Enum` bloku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud máte sadu neměnné hodnoty, které jsou logicky vzájemně souvisí, můžete je definovat společně ve výčtu. To umožňuje smysluplné názvy pro výčet a její členy, které se snadněji mějte na paměti, než jejich hodnot. Potom můžete členy výčtu na mnoha místech v kódu.  
  
 Výhody použití výčty patří:  
  
-   Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.  
  
-   Lze snadno ke změně hodnot v budoucnu.  
  
-   Díky kód snadněji číst, což znamená, že je méně pravděpodobné, že bude nutné zavést chyb.  
  
-   Zajišťuje kompatibilitu. Pokud používáte výčty, váš kód je méně pravděpodobné, že nezdaří, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.  
  
 Výčet má název, základní datový typ a sadu členů. Každý člen představuje konstantu.  
  
 Výčet deklarovat na třídy, struktury, modul nebo úroveň rozhraní mimo libovolná procedura je *člen výčtu*. Je členem třídy, struktury, modul nebo rozhraní, který deklaruje ho.  
  
 Výčty člen je přístupná z kdekoli v rámci třídy, struktury, modul nebo rozhraní. Kód mimo třída, struktura nebo modul kvalifikaci název člena výčtu s názvem třídy, struktury nebo modul. Nutnost používat plně kvalifikované názvy přidáním se můžete vyhnout [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) příkaz ke zdrojovému souboru.  
  
 Výčet deklarovat na úrovni oboru názvů, mimo třídy, struktury, modul nebo rozhraní, je členem oboru názvů, ve kterém se zobrazí.  
  
 *Deklarace kontextu* pro výčet musí být zdrojový soubor, obor názvů, třídy, struktury, modul nebo rozhraní a nemůže být procedury. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Můžete použít atributy výčet jako celek, ale ne její členové jednotlivě. Atribut přispívá informace metadat sestavení.  
  
## <a name="data-type"></a>Datový typ  
 `Enum` Příkaz můžou deklarovat datový typ výčtu. Každý člen má datový typ výčtu. Můžete zadat `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, nebo `UShort`.  
  
 Pokud nezadáte `datatype` pro výčet, každý člen má datový typ jeho `initializer`. Pokud zadáte oba `datatype` a `initializer`, datový typ `initializer` musí být převoditelná na `datatype`. Pokud ani `datatype` ani `initializer` je k dispozici, výchozí hodnota je typu dat `Integer`.  
  
## <a name="initializing-members"></a>Inicializace členů  
 `Enum` Příkaz můžete inicializovat obsah vybrané členy v `memberlist`. Používáte `initializer` k poskytování výraz přiřazení člena.  
  
 Pokud nezadáte `initializer` pro člena, Visual Basic inicializuje se buď na nulu (Pokud je první `member` v `memberlist`), nebo k hodnotě větší, jedna než bezprostředně před `member`.  
  
 Výraz zadaný v každé `initializer` může být libovolnou kombinací literály, ostatní konstanty, které jsou již definováni a členové výčtu, které jsou již definováni, včetně předchozí členem tento výčet. Aritmetické a logické operátory můžete kombinovat takové elementy.  
  
 Nemůžete použít proměnné nebo funkce v `initializer`. Nicméně můžete používat klíčová slova převodu jako třeba `CByte` a `CShort`. Můžete také použít `AscW` při volání s konstantní `String` nebo `Char` argument, vzhledem k tomu, který lze vyhodnotit v době kompilace.  
  
 Výčty nesmí mít hodnoty s plovoucí desetinnou čárkou. Pokud je členem přiřadit hodnotu s plovoucí desetinnou čárkou a `Option Strict` nastavená na on, dojde k chybě kompilátoru. Pokud `Option Strict` je vypnutý, hodnota je automaticky převeden na `Enum` typu.  
  
 Pokud hodnotu člena překračuje povolený rozsah pro základní datový typ, nebo pokud inicializovat kteréhokoli člena maximální hodnotě povolené základní datový typ, kompilátor ohlásí chybu.  
  
## <a name="modifiers"></a>Modifikátory  
 Třída, struktura, modulu a rozhraní člen výčty výchozí nastavení veřejný přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu. Namespace člen výčty výchozí friend přístupu. Můžete nastavit jejich úrovně přístupu na veřejné, ale ne na soukromé nebo chráněné. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Všechny členy výčtu musejí veřejný přístup, a všechny modifikátory přístupu nelze použít na ně. Pokud daný výčet má omezenější úroveň přístupu, ale úroveň přístupu zadaný výčet má přednost před.  
  
 Ve výchozím nastavení všechny výčty jsou typy a jejich pole jsou konstanty. Proto `Shared`, `Static`, a `ReadOnly` klíčová slova nelze použít v případě deklarace výčet nebo její členy.  
  
## <a name="assigning-multiple-values"></a>Přiřazení více hodnot  
 Výčty obvykle představují vzájemně se vylučuje hodnoty. Zahrnutím <xref:System.FlagsAttribute> atribut `Enum` deklaraci, můžete místo toho přiřadit více hodnot do instance výčtu. <xref:System.FlagsAttribute> Atribut určuje, že výčtu být považovány za bitové pole, který je sada příznaků. Toto nastavení se nazývá *bitové* výčty.  
  
 Když pomocí deklarace výčtů <xref:System.FlagsAttribute> atribut, doporučujeme, abyste používali zajišťuje 2, který je, 1, 2, 4, 8, 16 a tak dále, pro hodnoty. Doporučujeme také, že "Žádný" být název člena, jehož hodnota je 0. Další pokyny najdete v části <xref:System.FlagsAttribute> a <xref:System.Enum>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `Enum` příkaz. Všimněte si, že člen se označuje jako `EggSizeEnum.Medium`a ne jako `Medium`.  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Metoda v následujícím příkladu je mimo `Egg` třídy. Proto `EggSizeEnum` je plně kvalifikovaný jako `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Enum` příkaz k definování související sadu s názvem konstantní hodnoty. V takovém případě hodnoty jsou barev, které můžete zvolit návrh formuláře pro zadávání dat pro databázi.  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje hodnoty, které zahrnují kladné a záporné čísla.  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se `As` klauzule slouží k určení `datatype` výčtu.  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat bitové výčet. Více hodnot lze přiřadit k instanci bitové výčtu. `Enum` Zahrnuje deklaraci <xref:System.FlagsAttribute> atribut, který označuje, že výčtu lze považovat za sadu příznaků.  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu prochází výčet. Použije <xref:System.Enum.GetNames%2A> metoda k načtení pole názvy členů z výčtu, a <xref:System.Enum.GetValues%2A> k načtení pole hodnot členů.  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konstanty a výčty](../../../visual-basic/language-reference/constants-and-enumerations.md)
