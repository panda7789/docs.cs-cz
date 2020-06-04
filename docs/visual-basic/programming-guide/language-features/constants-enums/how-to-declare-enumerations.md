---
title: 'Postupy: Deklarace výčtů'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: c8f228c205c93adf7f2f555dc840a7daac61950b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414450"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Postupy: Deklarace výčtů (Visual Basic)
Vytvoříte výčet s `Enum` příkazem v oddílu deklarace třídy nebo modulu. V rámci metody nelze deklarovat výčet. Chcete-li určit příslušnou úroveň přístupu, použijte `Private` , `Protected` , `Friend` nebo `Public` .  
  
 `Enum`Typ má název, nadřízený typ a sadu polí, z nichž každý představuje konstantu. Název musí být platným kvalifikátorem Visual Basic .NET. Nadřízený typ musí být jeden z celočíselných typů – `Byte` , `Short` `Long` nebo `Integer` . `Integer` je výchozí možnost. Výčty jsou vždy silného typu a nejsou zaměnitelné s celočíselnými typy čísel.  
  
 Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou. Pokud je výčtu přiřazena hodnota s plovoucí desetinnou čárkou `Option Strict On` , výsledkem je chyba kompilátoru. Pokud `Option Strict` je `Off` , hodnota je automaticky převedena na `Enum` typ.  
  
 Informace o názvech a o tom, jak použít `Imports` příkaz k zajištění nepotřebné kvalifikace názvu, najdete v tématu [výčty a kvalifikace názvu](enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Deklarace výčtu  
  
1. Napište deklaraci, která obsahuje úroveň přístupu kódu, `Enum` klíčové slovo a platný název, jako v následujících příkladech, z nichž každý deklaruje jiný `Enum` .  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Definujte konstanty ve výčtu. Ve výchozím nastavení je první konstanta ve výčtu inicializována na `0` a další konstanty jsou inicializovány na hodnotu jednoho z více než předchozí konstanty. Například následující výčet `Days` obsahuje konstantu s názvem `Sunday` s hodnotou `0` , konstanta s názvem, `Monday` `1` konstanta s `Tuesday` hodnotou a `2` tak dále.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Můžete explicitně přiřadit hodnoty konstantám ve výčtu pomocí příkazu přiřazení. Můžete přiřadit libovolné celočíselné hodnoty, včetně záporných čísel. Například může být vhodné, aby konstanty s hodnotami menšími než nula představovaly chybové stavy. V následujícím výčtu je konstantě `Invalid` explicitně přiřazena hodnota `–1` a konstanta `Sunday` je přiřazena hodnota `0` . Vzhledem k tomu, že se jedná o první konstantu ve výčtu, `Saturday` je také inicializována na hodnotu `0` . Hodnota `Monday` je `1` (jedna hodnota `Sunday` ) `Tuesday` , hodnota je `2` , a tak dále.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Deklarace výčtu jako explicitního typu  
  
- Zadejte typ výčtu pomocí `As` klauzule, jak je znázorněno v následujícím příkladu.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Postupy: Odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md)
- [Postupy: Iterace ve výčtu jazyka Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](when-to-use-an-enumeration.md)
- [Přehled konstant](constants-overview.md)
- [Datové typy konstanty a literálu](constant-and-literal-data-types.md)
- [Konstanty a výčty](../../../language-reference/constants-and-enumerations.md)
