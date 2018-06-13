---
title: 'Postupy: Deklarace výčtů (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: e2dbdbbf6bf7fe3e4b71cbe7edc7a19b18f96ef2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650800"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Postupy: Deklarace výčtů (Visual Basic)
Vytvoření výčtu s `Enum` příkazu v části deklarace třídy nebo modulu. Výčet v rámci metodu nelze deklarovat. Pokud chcete zadat odpovídající úroveň přístupu, použijte `Private`, `Protected`, `Friend`, nebo `Public`.  
  
 `Enum` Typ má název, typ základní a sady polí, každý reprezentující konstantu. Název musí být platný kvalifikátor Visual Basic .NET. Základní typ musí být jeden z typů celé číslo –`Byte`, `Short`, `Long` nebo `Integer`. `Integer` je výchozí. Výčty jsou vždy silného typu a se nedají zaměňovat s typy číslo celé číslo.  
  
 Výčty nesmí mít hodnoty s plovoucí desetinnou čárkou. Pokud je výčet přiřazenou hodnotu s plovoucí desetinnou čárkou s `Option Strict On`, výsledků chyby kompilátoru. Pokud `Option Strict` je `Off`, hodnota je automaticky převeden na `Enum` typu.  
  
 Informace o názvech a jak používat `Imports` najdete v části prohlášení není zapotřebí, aby kvalifikace názvu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Chcete-li deklarace výčtů  
  
1.  Zápis deklaraci, která zahrnuje úroveň přístupu kódu, `Enum` – klíčové slovo a platný název, jako v následujících příkladech, z nichž každý deklaruje jiné `Enum`.  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  Definujte konstanty ve výčtu. Ve výchozím nastavení, je inicializováno první konstanta ve výčtu `0`, a následné konstanty jsou inicializována tak, aby na hodnotu jedna víc než předchozí konstanta. Například následující výčet `Days`, obsahuje konstanta s názvem `Sunday` s hodnotou `0`, konstanta s názvem `Monday` s hodnotou `1`, konstanta s názvem `Tuesday` s hodnotou `2`a tak dále.  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  Můžete explicitně přiřadit hodnoty konstant ve výčtu pomocí příkazu přiřazení. Můžete přiřadit jakékoli celé číslo, včetně záporná čísla. Například můžete konstanty hodnoty menší než nula představují chybové stavy. V následující výčet konstanta `Invalid` je explicitně přiřazena hodnota `–1`a konstantu `Sunday` je přiřazena hodnota `0`. Protože se jedná o první konstanta ve výčtu, `Saturday` je také inicializován na hodnotu `0`. Hodnota `Monday` je `1` (jednu vyšší než hodnota `Sunday`); hodnota `Tuesday` je `2`a tak dále.  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Chcete-li deklarovat výčet jako explicitního typu  
  
-   Zadejte typ výčtového typu pomocí `As` klauzule, jak je znázorněno v následujícím příkladu.  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Postupy: iterace výčet v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
