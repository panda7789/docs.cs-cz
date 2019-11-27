---
title: Uživatelem definované konstanty
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 194a420b3749ca5c858a65c07b8c164287c1582a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354010"
---
# <a name="user-defined-constants-visual-basic"></a>Uživatelem definované konstanty (Visual Basic)
Konstanta je smysluplný název, který přebírá místo čísla nebo řetězce, který se nemění. Konstanty ukládají hodnoty, které jako název implikují, zůstávají během provádění aplikace konstantní. Můžete použít konstanty, které jsou definovány ovládacími prvky nebo komponentami, se kterými pracujete, nebo můžete vytvořit vlastní. Konstanty, které vytvoříte sami, jsou popsány jako *uživatelsky definované*.  
  
 Deklarujete konstantu pomocí příkazu `Const` a použijete stejné pokyny jako pro vytvoření názvu proměnné. Pokud je `Option Strict` `On`, musíte explicitně deklarovat typ konstanty.  
  
## <a name="const-statement-usage"></a>Použití příkazu const  
 Příkaz `Const` může představovat matematické nebo datum a čas:  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 Může také definovat `String` konstanty:  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 Výraz na pravé straně znaménka rovná se (`=`) je často číslo nebo literální řetězec, ale může to být výraz, jehož výsledkem je číslo nebo řetězec (i když tento výraz nemůže obsahovat volání funkcí). Můžete dokonce definovat konstanty z podmínek dříve definovaných konstant:  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>Rozsah uživatelsky definovaných konstant  
 Obor příkazu `Const` je stejný jako objekt proměnné deklarované ve stejném umístění. Rozsah můžete zadat některým z následujících způsobů:  
  
- Chcete-li vytvořit konstantu, která existuje pouze v rámci procedury, deklarujte ji v rámci tohoto postupu.  
  
- Chcete-li vytvořit konstantu dostupnou pro všechny postupy v rámci třídy, ale ne pro žádný kód mimo tento modul, deklarujte ho v oddílu deklarace třídy.  
  
- Chcete-li vytvořit konstantu, která je k dispozici pro všechny členy sestavení, ale ne pro externí klienty sestavení, deklarujte ji pomocí klíčového slova `Friend` v oddílu deklarace třídy.  
  
- Chcete-li vytvořit konstantu dostupnou v celé aplikaci, deklarujte ji pomocí klíčového slova `Public` v oddílu deklarace třídy.  
  
 Další informace naleznete v tématu [How to: Declare a konstante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Zamezení cyklických odkazů  
 Vzhledem k tomu, že konstanty lze definovat v souvislosti s jinými konstantami, je možné neúmyslně vytvořit *cyklus*nebo cyklický odkaz mezi dvěma nebo více konstantami. K cyklu dochází, když máte dvě nebo více veřejných konstant, z nichž každá je definována z hlediska druhé, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 Pokud dojde k cyklu, Visual Basic vygeneruje chybu kompilátoru.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Konstanty a výčty](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Postupy: deklarace výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
