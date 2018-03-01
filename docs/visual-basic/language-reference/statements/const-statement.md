---
title: "Const – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 720a465f1459b663a1fca2a48856f51762328459
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="const-statement-visual-basic"></a>Const – příkaz (Visual Basic)
Deklaruje a definuje jeden nebo více konstanty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. Seznam atributů, které platí pro všechny konstanty deklarované v tomto příkazu. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").  
  
 `accessmodifier`  
 Volitelné. Slouží k určení, k jaké kód přístup tyto konstanty. Může být [veřejné](../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, nebo [privátní](../../../visual-basic/language-reference/modifiers/private.md).  
  
 `Shadows`  
 Volitelné. Použijte redeclare a skrýt programovací element v základní třídě. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Požadováno. Seznam konstanty se deklarované v tomto příkazu.  
  
 `constant``[ ,``constant``... ]`  
  
 Každý `constant` má následující syntaxe a částí:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Část|Popis|  
|----------|-----------------|  
|`constantname`|Požadováno. Název konstanty. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Požadováno pokud `Option Strict` je `On`. Datový typ konstanty.|  
|`initializer`|Požadováno. Výraz, který se vyhodnotí v době kompilace a přiřadí do konstanta.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud máte hodnotu, která nikdy změny ve vaší aplikaci, můžete definovat pojmenované konstanty a používejte místo je Literálová hodnota. Název je snazší mějte na paměti, než hodnotu. Můžete definovat konstanta pouze jednou a použít na mnoha místech v kódu. Pokud v novější verzi, budete muset znovu definovat hodnotu, `Const` příkaz je jediným místem, budete muset udělat změnu.  
  
 Můžete použít `Const` pouze na úrovni modulu nebo procedury. To znamená *deklarace kontextu* pro proměnnou, musí být třída, struktura, modulu, postup nebo bloku a nemůže být zdrojový soubor, obor názvů nebo rozhraní. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Výchozí místní konstanty (uvnitř procedury) veřejný přístup, a nelze použít žádné modifikátory přístupu na ně. Třídy a modul výchozí konstanty (mimo libovolná procedura) člena privátní přístup a struktura člen konstanty výchozí nastavení veřejný přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Konstanta deklarovat na úrovni modulu, mimo libovolná procedura je *člen konstanta*; je členem třídy, struktury, nebo modul, který ji deklaruje.  
  
     Konstanta deklarovat na úroveň procedury je *místní konstanta*; je místní pro proceduru nebo blok, který deklaruje ho.  
  
-   **Atributy.** Atributy můžete použít pouze k člen konstanty, nikoli k místním konstanty. Atribut přispívá informace metadat sestavení, která není smysl pro dočasné úložiště, jako je například místní konstanty.  
  
-   **Modifikátory.** Ve výchozím nastavení jsou všechny konstanty `Shared`, `Static`, a `ReadOnly`. Nemůžete použít žádnou z těchto klíčových slov při deklarování konstanta.  
  
     Na úrovni postup, nemůžete použít `Shadows` nebo žádný přístup modifikátory deklarovat místní konstanty.  
  
-   **Více konstanty.** Je možné deklarovat několik konstanty v jednom příkazu deklaraci určující `constantname` část pro každé z nich. Více konstanty jsou oddělené čárkami.  
  
## <a name="data-type-rules"></a>Datový typ pravidla  
  
-   **Datové typy.** `Const` Příkaz můžou deklarovat datový typ proměnné. Můžete zadat jakýkoli datový typ nebo název výčtu.  
  
-   **Výchozí typ.** Pokud nezadáte `datatype`, konstanta trvá datový typ `initializer`. Pokud zadáte oba `datatype` a `initializer`, datový typ `initializer` musí být převoditelná na `datatype`. Pokud ani `datatype` ani `initializer` je k dispozici, výchozí hodnota je typu dat `Object`.  
  
-   **Různé typy.** Můžete zadat různé datové typy pro různé konstanty pomocí samostatné `As` klauzule pro každou proměnnou můžete deklarovat. Však nelze deklarovat několik konstanty být stejného typu pomocí společného `As` klauzule.  
  
-   **Inicializace.** Je třeba inicializovat hodnotu každých konstanta ve `constantlist`. Používáte `initializer` k poskytování výraz přiřazení konstanta. Výraz může být libovolnou kombinací literály, ostatní konstanty, které jsou již definováni a členové výčtu, které jsou již definováni. Aritmetické a logické operátory můžete kombinovat takové elementy.  
  
     Nemůžete použít proměnné nebo funkce v `initializer`. Nicméně můžete používat klíčová slova převodu jako třeba `CByte` a `CShort`. Můžete také použít `AscW` při volání s konstantní `String` nebo `Char` argument, vzhledem k tomu, který lze vyhodnotit v době kompilace.  
  
## <a name="behavior"></a>Chování  
  
-   **Rozsah.** Místní konstanty jsou k dispozici pouze v rámci postupu nebo bloku. Konstanty člen jsou přístupné z libovolné místo v rámci své třídy, struktury nebo modul.  
  
-   **Kvalifikace.** Kód mimo třída, struktura, modul nebo kvalifikaci název konstanta člen s názvem třídy, struktury nebo modul. Mimo území procedura nebo bloku nemůže odkazovat na jakékoli místní konstanty v rámci tohoto postupu nebo bloku kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Const` příkaz deklarovat konstanty pro použití místo literálových hodnot.  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Pokud definujete konstanta s datovým typem `Object`, Visual Basic – kompilátor poskytuje typ `initializer`, místo `Object`. V následujícím příkladu konstanta `naturalLogBase` má typ spuštění `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 V předchozím příkladu používá <xref:System.Type.ToString%2A> metodu <xref:System.Type> objekt vrácený [gettype – operátor](../../../visual-basic/language-reference/operators/gettype-operator.md), protože <xref:System.Type> nelze převést na `String` pomocí `CStr`.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [#Const – direktiva](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim – příkaz](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Konstanty a výčty](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [Konstanty a výčty](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
