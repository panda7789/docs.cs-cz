---
title: 'Postupy: Deklarace výčtů'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 042aea045313bcaf3832274acf1000f87a084b72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354047"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Postupy: Deklarace výčtů (Visual Basic)
Vytvoříte výčet pomocí příkazu `Enum` v oddílu deklarace třídy nebo modulu. V rámci metody nelze deklarovat výčet. K určení odpovídající úrovně přístupu použijte `Private`, `Protected`, `Friend`nebo `Public`.  
  
 Typ `Enum` má název, nadřízený typ a sadu polí, z nichž každý představuje konstantu. Název musí být platným kvalifikátorem Visual Basic .NET. Nadřízený typ musí být jeden z celočíselných typů –`Byte`, `Short`, `Long` nebo `Integer`. výchozím nastavením je `Integer`. Výčty jsou vždy silného typu a nejsou zaměnitelné s celočíselnými typy čísel.  
  
 Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou. Pokud je výčtu přiřazena hodnota s plovoucí desetinnou čárkou s `Option Strict On`, výsledkem bude chyba kompilátoru. Je-li `Option Strict` `Off`, hodnota je automaticky převedena na typ `Enum`.  
  
 Informace o názvech a o tom, jak použít příkaz `Imports` k zajištění nepotřebné kvalifikace názvu, naleznete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Deklarace výčtu  
  
1. Napište deklaraci, která obsahuje úroveň přístupu kódu, klíčové slovo `Enum` a platný název, jako v následujících příkladech, z nichž každý deklaruje jiný `Enum`.  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Definujte konstanty ve výčtu. Ve výchozím nastavení je první konstanta ve výčtu inicializována na `0`a následné konstanty jsou inicializovány na hodnotu jednoho z více než předchozí konstanty. Například následující výčet `Days`obsahuje konstantu s názvem `Sunday` s hodnotou `0`, konstanta s názvem `Monday` s hodnotou `1`, konstanta s názvem `Tuesday` s hodnotou `2`a tak dále.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Můžete explicitně přiřadit hodnoty konstantám ve výčtu pomocí příkazu přiřazení. Můžete přiřadit libovolné celočíselné hodnoty, včetně záporných čísel. Například může být vhodné, aby konstanty s hodnotami menšími než nula představovaly chybové stavy. V následujícím výčtu je konstantě `Invalid` explicitně přiřazena hodnota `–1`a k konstantě `Sunday` je přiřazena hodnota `0`. Vzhledem k tomu, že se jedná o první konstantu ve výčtu, `Saturday` je také inicializována na hodnotu `0`. Hodnota `Monday` je `1` (více než hodnota `Sunday`); hodnota `Tuesday` je `2`atd.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Deklarace výčtu jako explicitního typu  
  
- Zadejte typ výčtu pomocí klauzule `As`, jak je znázorněno v následujícím příkladu.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Postupy: iterace prostřednictvím výčtu v Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
