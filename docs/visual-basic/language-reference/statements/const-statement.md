---
title: Const – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 089c2dca99373f379e1eff319cf8c41242e5f135
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835307"
---
# <a name="const-statement-visual-basic"></a>Const – příkaz (Visual Basic)
Deklaruje a definuje jeden nebo více konstant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. Seznam atributů, které se vztahují na všechny konstanty deklarované v tomto prohlášení. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").  
  
 `accessmodifier`  
 Volitelné. Slouží k určení, jaký kód může přistupovat k těmto konstanty. Může být [veřejné](../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [privátní](../../../visual-basic/language-reference/modifiers/private.md), nebo [Private, Protected](../../language-reference/modifiers/private-protected.md).
  
 `Shadows`  
 Volitelné. Použijte pro předeklarovat a skrýt programovací element v základní třídě. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Povinný parametr. Seznam konstant deklarované v tomto prohlášení.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Každý `constant` má následující syntaxi a části:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Část|Popis|  
|----------|-----------------|  
|`constantname`|Povinný parametr. Název konstanty. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Požadováno pokud `Option Strict` je `On`. Datový typ konstanty.|  
|`initializer`|Povinný parametr. Výraz, který je vyhodnocen v době kompilace a přiřazený konstantě.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud máte ve své aplikaci hodnotu, která se nikdy nemění, můžete definovat pojmenované konstanty a použít místo literálovou hodnotou. Název je snazší než hodnota mějte na paměti. Můžete definovat konstantu pouze jednou a použít ji na mnoha místech ve vašem kódu. Pokud v novější verzi, je potřeba znovu definovat hodnotu, `Const` příkaz je jediným místem, budete muset provést změnu.  
  
 Můžete použít `Const` pouze na úrovni modulu nebo proceduru. To znamená, že *kontext deklarace* pro proměnnou musí být třída, struktura, modulu, proceduru nebo blok a nemůže být zdrojový soubor, obor názvů nebo rozhraní. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Místní konstanty (uvnitř procedury) výchozí veřejný přístup, a nemůže používat žádné modifikátory přístupu na nich. Třídy a modul výchozí konstanty (mimo všechny procedury) člen privátní přístup a struktura členské konstanty výchozí veřejný přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu.  
  
## <a name="rules"></a>pravidla  
  
-   **Místní deklarace.** Konstanta deklarovanou na úrovni modulu, mimo všechny procedury, je *členské konstanty*; je členem třídy, struktury, nebo modul, který je deklaruje.  
  
     Konstanta deklarované na úroveň procedury je *lokální konstanta*; je místní pro proceduru nebo blok, který deklaruje ho.  
  
-   **Atributy.** Můžete použít atributy pouze na členské konstanty, nikoli na místní konstanty. Atribut přispívá informace metadat sestavení, která není smysl pro dočasné úložiště, jako je například místní konstanty.  
  
-   **Modifikátory.** Standardně jsou všechny konstanty `Shared`, `Static`, a `ReadOnly`. Nemůžete použít žádnou z těchto klíčových slov při deklarování konstantní.  
  
     Na úrovni postupu nelze použít `Shadows` nebo žádný přístup k modifikátory deklarovat lokální konstanty.  
  
-   **Více konstant.** Je možné deklarovat několik konstant ve stejném příkazu deklarace, určení `constantname` část pro každé z nich. Více konstant jsou odděleny čárkami.  
  
## <a name="data-type-rules"></a>Datový typ pravidla  
  
-   **Datové typy.** `Const` Příkazu můžete deklarovat datový typ proměnné. Můžete zadat libovolný datový typ nebo název výčtu.  
  
-   **Výchozí typ.** Pokud nezadáte `datatype`, konstanta má datový typ `initializer`. Pokud zadáte obě `datatype` a `initializer`, datový typ `initializer` musí být převeditelný na `datatype`. Pokud ani `datatype` ani `initializer` je k dispozici, výchozí hodnota je typu dat `Object`.  
  
-   **Různé typy.** Můžete určit různé datové typy pro různé konstanty pomocí samostatné `As` klauzuli pro každou proměnnou můžete deklarovat. Nelze však deklarovat několik konstant bude stejného typu pomocí společného `As` klauzuli.  
  
-   **Inicializace.** Hodnota v každé konstanty musí inicializovat `constantlist`. Použijete `initializer` zadat výraz, který se přidělí na konstantu. Výraz může obsahovat libovolnou kombinaci literály, jiné konstanty, které jsou již definovány a členy výčtu, které jsou již definovány. Aritmetické a logické operátory můžete kombinovat takovýchto prvků.  
  
     Nelze použít proměnné nebo funkce v `initializer`. Ale můžete použít klíčová slova převodu například `CByte` a `CShort`. Můžete také použít `AscW` při volání s konstantou `String` nebo `Char` argument, protože, který může být vyhodnocen v době kompilace.  
  
## <a name="behavior"></a>Chování  
  
-   **Obor.** Místní konstanty je přístupný jenom v rámci jejich proceduru nebo blok. Členské konstanty jsou přístupné z kamkoli v jejich třídy, struktury nebo modulu.  
  
-   **Kvalifikace.** Kód mimo třídu, strukturu nebo modul musí kvalifikovat název člena konstanta s názvem této třídy, struktury nebo modulu. Kód mimo území proceduru nebo blok nemůže odkazovat na žádné místní konstanty v rámci tohoto postupu nebo bloku.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Const` příkaz k deklaraci konstanty pro použití namísto hodnoty literálu.  
  
 [!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]  
  
## <a name="example"></a>Příklad  
 Je-li definovat konstantu s datovým typem `Object`, kompilátor jazyka Visual Basic poskytuje typ `initializer`, namísto `Object`. V následujícím příkladu, konstanta `naturalLogBase` má run-time typu `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]  
  
 V předchozím příkladu <xref:System.Type.ToString%2A> metodu na <xref:System.Type> objekt vrácený [GetType – operátor](../../../visual-basic/language-reference/operators/gettype-operator.md), protože <xref:System.Type> nelze převést na `String` pomocí `CStr`.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Konstanty a výčty](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Konstanty a výčty](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
