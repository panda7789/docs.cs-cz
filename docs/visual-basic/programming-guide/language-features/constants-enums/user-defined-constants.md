---
title: Uživatelem definované konstanty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: dc940105bbeb5e54819b8df5d5b3c831c7a6e145
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527312"
---
# <a name="user-defined-constants-visual-basic"></a>Uživatelem definované konstanty (Visual Basic)
Konstanta je smysluplný název, který probíhá číslo nebo řetězec, který se nemění. Konstanty ukládání hodnot, které, jak již název napovídá, zůstanou neměnný po celou dobu spuštění aplikace. Můžete použít konstanty, které jsou definovány ovládací prvky nebo komponenty, které můžete pracovat, nebo můžete vytvořit svoje vlastní. Konstanty, které si sami vytvoříte, jsou popsány jako *uživatelem definované*.  
  
 Deklarace konstanty s `Const` příkaz pomocí stejné pokyny jako byste to udělali pro vytvoření názvu proměnné. Pokud `Option Strict` je `On`, musíte explicitně deklarovat typ konstanty.  
  
## <a name="const-statement-usage"></a>Const – příkaz využití  
 A `Const` příkaz může představovat matematické nebo datum a čas, množství:  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 Je také definovat `String` konstanty:  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 Výraz na pravé straně znaménka rovnosti ( `=` ) je často číslo nebo řetězcový literál, ale také může být výraz, jehož výsledkem číslo nebo řetězec (i když tento výraz nemůže obsahovat volání funkcí). Můžete dokonce definovat konstanty z hlediska dříve definované konstanty:  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>Rozsah uživatelem definované konstanty  
 A `Const` obor příkazu je stejné jako u proměnné deklarované ve stejném umístění. Zadejte rozsah v některém z následujících způsobů:  
  
-   Chcete-li vytvořit konstantu, která existuje pouze v rámci procedury, deklarujte ho v rámci tohoto postupu.  
  
-   K vytvoření konstantu k dispozici pro všechny postupy v rámci třídy, ale ne k žádným kódem mimo modul, ji deklarujte v sekci prohlášení třídy.  
  
-   Pokud chcete vytvořit konstantu, která je k dispozici všem členům sestavení, ale ne ke klientům mimo sestavení, deklarujete jej s použitím `Friend` – klíčové slovo v sekci prohlášení třídy.  
  
-   Pokud chcete vytvořit konstantní k dispozici v celé aplikaci, deklarujete jej s použitím `Public` části – klíčové slovo v deklaracích třídy.  
  
 Další informace najdete v tématu [jak: Deklarace konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Jak se vyhnout cyklické odkazy  
 Protože jde o dalších konstant lze definovat konstanty, je možné neúmyslně vytvořit *cyklu*, nebo cyklický odkaz mezi dva nebo více konstant. Cyklus dojde, pokud mají dvě nebo více veřejné konstanty, z nichž každý je definována v jiné, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Pokud dochází k zacyklení, Visual Basic vygeneruje chybu kompilátoru.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Konstanty a výčty](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Postupy: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
