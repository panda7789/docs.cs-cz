---
title: 'Postupy: Deklarace výčtů (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: d309e4fb09bc0b8af87422bc84427528deb29e7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710310"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Postupy: Deklarace výčtů (Visual Basic)
Vytvořit výčet s `Enum` příkazu v části deklarace třídy nebo modulu. Nelze deklarovat výčet v rámci metody. Pokud chcete zadat odpovídající úroveň přístupu, použijte `Private`, `Protected`, `Friend`, nebo `Public`.  
  
 `Enum` Typ má název, nadřízený typ a sadu polí, každý představuje konstantu. Název musí být platný kvalifikátor Visual Basic .NET. Základní typ musí být jeden z typů celé číslo –`Byte`, `Short`, `Long` nebo `Integer`. `Integer` je výchozí nastavení. Výčty jsou vždy silného typu a se nedají zaměňovat s číselné typy celých čísel.  
  
 Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou. Pokud výčtu je přiřazena hodnota s plovoucí desetinnou čárkou s `Option Strict On`, výsledcích chyb kompilátoru. Pokud `Option Strict` je `Off`, hodnota je automaticky převedena na `Enum` typu.  
  
 Informace o názvech a jak používat `Imports` naleznete v tématu příkazu nezbytné, aby kvalifikace názvu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Chcete-li deklarovat výčet  
  
1.  Zápis deklarace, která zahrnuje úroveň přístupu kódu, `Enum` – klíčové slovo a platný název, jako v následujících příkladech, z nichž každý deklaruje jiný `Enum`.  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  Definujte konstanty ve výčtu. Ve výchozím nastavení, první konstanta ve výčtu je inicializován na `0`, a následné konstanty jsou inicializovány na hodnotu některého jiného než předchozí – konstanta. Například následující výčet `Days`, obsahuje konstanty s názvem `Sunday` s hodnotou `0`, konstanta s názvem `Monday` s hodnotou `1`, konstanta s názvem `Tuesday` s hodnotou `2`, a tak dále.  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  Můžete explicitně přiřadit hodnoty konstant ve výčtu s použitím příkazu přiřazení. Můžete přiřadit libovolnou celočíselnou hodnotu, včetně záporná čísla. Například můžete konstanty s hodnoty menší než nula, která představuje chybové stavy. V následující výčet konstanty `Invalid` explicitně přiřazena hodnota `–1`a konstanty `Sunday` je přiřazena hodnota `0`. Protože se jedná o první konstanta výčtu, `Saturday` je také inicializován na hodnotu `0`. Hodnota `Monday` je `1` (jedno více než hodnota `Sunday`); hodnota `Tuesday` je `2`, a tak dále.  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Chcete-li deklarovat výčet jako explicitní typ  
  
-   Zadejte typ výčtu s použitím `As` klauzule, jak je znázorněno v následujícím příkladu.  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Postupy: Iterace ve výčtu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
