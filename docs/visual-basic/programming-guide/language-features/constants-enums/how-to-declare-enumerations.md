---
title: "Postupy: Deklarace výčtů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 938550ebbfcf099729db3de96b809549cb234d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Postupy: Deklarace výčtů (Visual Basic)
Vytvoření výčtu s `Enum` příkazu v části deklarace třídy nebo modulu. Výčet v rámci metodu nelze deklarovat. Pokud chcete zadat odpovídající úroveň přístupu, použijte `Private`, `Protected`, `Friend`, nebo `Public`.  
  
 `Enum` Typ má název, typ základní a sady polí, každý reprezentující konstantu. Název musí být platný kvalifikátor Visual Basic .NET. Základní typ musí být jeden z typů celé číslo –`Byte`, `Short`, `Long` nebo `Integer`. `Integer`je výchozí. Výčty jsou vždy silného typu a se nedají zaměňovat s typy číslo celé číslo.  
  
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
 [Postupy: odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Postupy: iterace výčet v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Postupy: určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
