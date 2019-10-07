---
title: Const – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 522ac71767707ae90a3f1d11d45ef8b29471ae6c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005124"
---
# <a name="const-statement-visual-basic"></a>Const – příkaz (Visual Basic)
Deklaruje a definuje jednu nebo více konstant.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. Seznam atributů, které se vztahují na všechny konstanty deklarované v tomto příkazu. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`" a "`>`").  
  
 `accessmodifier`  
 Volitelné. Toto použijte k určení, ke kterému kódu má přístup k těmto konstantám. Může být [Veřejná](../../../visual-basic/language-reference/modifiers/public.md), [chráněná](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../../../visual-basic/language-reference/modifiers/private.md)nebo [Private Protected](../../language-reference/modifiers/private-protected.md).
  
 `Shadows`  
 Volitelné. Použijte k předeklaraci a skrytí programovacího prvku v základní třídě. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Požadováno. Seznam konstant, které jsou deklarovány v tomto příkazu.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Každý `constant` má následující syntaxi a části:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Částí|Popis|  
|----------|-----------------|  
|`constantname`|Požadováno. Název konstanty. Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Vyžaduje se, pokud je `Option Strict` `On`. Datový typ konstanty.|  
|`initializer`|Požadováno. Výraz vyhodnocený v době kompilace a přiřazený konstantě|  
  
## <a name="remarks"></a>Poznámky  
 Pokud máte hodnotu, která se ve vaší aplikaci nikdy nemění, můžete definovat pojmenovanou konstantu a použít ji místo hodnoty literálu. Název je snazší pamatovat než hodnota. Konstantu můžete definovat pouze jednou a použít ji na mnoha místech kódu. Pokud v novější verzi potřebujete předefinovat hodnotu, je příkaz `Const` jediným místem, kde je třeba provést změnu.  
  
 @No__t-0 můžete použít pouze v modulu nebo v úrovni procedury. To znamená, že *kontext deklarace* proměnné musí být třída, struktura, modul, procedura nebo blok a nemůže se jednat o zdrojový soubor, obor názvů nebo rozhraní. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Místní konstanty (uvnitř procedury) jako výchozí pro veřejný přístup a nemůžete použít žádné modifikátory přístupu. Konstanty členů třídy a modulu (mimo jakákoli procedura) výchozí pro privátní přístup a členské konstanty struktury jsou standardně přístupné pro veřejný přístup. Můžete upravit jejich úrovně přístupu modifikátory přístupu.  
  
## <a name="rules"></a>Pravidly  
  
- **Kontext deklarace** Konstanta deklarovaná na úrovni modulu, mimo jakoukoli proceduru, je *členská konstanta*; je členem třídy, struktury nebo modulu, který je deklaruje.  
  
     Konstanta deklarovaná na úrovni procedury je *místní konstanta*; je místní pro proceduru nebo blok, který je deklaruje.  
  
- **Atribut.** Atributy lze použít pouze pro členské konstanty, nikoli pro místní konstanty. Atribut přispívá k metadatům sestavení, která nejsou smysluplná pro dočasné úložiště, jako jsou například místní konstanty.  
  
- **Modifikátory.** Ve výchozím nastavení jsou všechny konstanty `Shared`, `Static` a `ReadOnly`. Při deklaraci konstanty nemůžete použít žádná z těchto klíčových slov.  
  
     Na úrovni procedury nemůžete použít `Shadows` ani žádné modifikátory přístupu k deklaraci místních konstant.  
  
- **Několik konstant.** Můžete deklarovat několik konstant v rámci jednoho příkazu deklarace, přičemž pro každou z nich určíte část `constantname`. Vícenásobné konstanty jsou odděleny čárkami.  
  
## <a name="data-type-rules"></a>Pravidla datového typu  
  
- **Datové typy.** Příkaz `Const` může deklarovat datový typ proměnné. Můžete zadat libovolný datový typ nebo název výčtu.  
  
- **Výchozí typ** Pokud nezadáte `datatype`, konstanta převezme datový typ `initializer`. Pokud zadáte obě `datatype` i `initializer`, datový typ `initializer` musí být převeden na `datatype`. Pokud není k dispozici žádná `datatype` ani `initializer`, datový typ se nastaví jako výchozí `Object`.  
  
- **Různé typy.** Pro každou proměnnou, kterou deklarujete, můžete určit různé typy dat pro různé @no__t konstanty. Některé konstanty však nelze deklarovat jako stejný typ pomocí běžné klauzule `As`.  
  
- **Operace.** Je nutné inicializovat hodnotu každé konstanty v `constantlist`. Pomocí `initializer` můžete zadat výraz, který se má přiřadit konstantě. Výraz může být libovolná kombinace literálů, dalších konstant, které jsou již definovány, a členů výčtu, které jsou již definovány. K kombinování takových prvků lze použít aritmetické a logické operátory.  
  
     V `initializer` nemůžete použít proměnné ani funkce. Můžete však použít klíčová slova převodu, například `CByte` a `CShort`. @No__t-0 můžete použít také v případě, že ho zavoláte s konstantním argumentem `String` nebo `Char`, protože je možné ho vyhodnotit v době kompilace.  
  
## <a name="behavior"></a>Předvídatelně  
  
- **Oboru.** Místní konstanty jsou přístupné pouze v rámci jejich procedury nebo bloku. Konstanty členů jsou přístupné odkudkoli v rámci své třídy, struktury nebo modulu.  
  
- **Vydal.** Kód mimo třídu, strukturu nebo modul musí kvalifikovat název členské konstanty s názvem této třídy, struktury nebo modulu. Kód mimo proceduru nebo blok nemůže odkazovat na žádné místní konstanty v rámci tohoto postupu nebo bloku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Const` k deklaraci konstant pro použití namísto hodnot literálu.  
  
 [!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]  
  
## <a name="example"></a>Příklad  
 Definujete-li konstantu s datovým typem `Object`, kompilátor Visual Basic mu místo `Object` poskytne typ `initializer`. V následujícím příkladu konstanta `naturalLogBase` má běhový typ `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]  
  
 Předchozí příklad používá metodu <xref:System.Type.ToString%2A> u objektu <xref:System.Type> vráceného [operátorem GetType](../../../visual-basic/language-reference/operators/gettype-operator.md), protože <xref:System.Type> nelze převést na `String` pomocí `CStr`.  
  
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
