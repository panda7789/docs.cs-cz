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
ms.openlocfilehash: 14f3de39eb8d8e6820e2b40792a8e8e57217e410
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414373"
---
# <a name="user-defined-constants-visual-basic"></a>Uživatelem definované konstanty (Visual Basic)
Konstanta je smysluplný název, který přebírá místo čísla nebo řetězce, který se nemění. Konstanty ukládají hodnoty, které jako název implikují, zůstávají během provádění aplikace konstantní. Můžete použít konstanty, které jsou definovány ovládacími prvky nebo komponentami, se kterými pracujete, nebo můžete vytvořit vlastní. Konstanty, které vytvoříte sami, jsou popsány jako *uživatelsky definované*.  
  
 Deklaraci konstanty pomocí příkazu deklarujete `Const` pomocí stejných pokynů, které byste chtěli pro vytvoření názvu proměnné. Pokud `Option Strict` je `On` , musíte explicitně deklarovat typ konstanty.  
  
## <a name="const-statement-usage"></a>Použití příkazu const  
 `Const`Příkaz může představovat matematické nebo časové množství data a času:  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 Může také definovat `String` konstanty:  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 Výraz na pravé straně znaménka rovná se ( `=` ) je často číslo nebo literální řetězec, ale může to být výraz, jehož výsledkem je číslo nebo řetězec (i když tento výraz nemůže obsahovat volání funkcí). Můžete dokonce definovat konstanty z podmínek dříve definovaných konstant:  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>Rozsah uživatelsky definovaných konstant  
 `Const`Obor příkazu je stejný jako objekt proměnné deklarované ve stejném umístění. Rozsah můžete zadat některým z následujících způsobů:  
  
- Chcete-li vytvořit konstantu, která existuje pouze v rámci procedury, deklarujte ji v rámci tohoto postupu.  
  
- Chcete-li vytvořit konstantu dostupnou pro všechny postupy v rámci třídy, ale ne pro žádný kód mimo tento modul, deklarujte ho v oddílu deklarace třídy.  
  
- Chcete-li vytvořit konstantu, která je k dispozici pro všechny členy sestavení, ale ne pro externí klienty sestavení, deklarujte ji pomocí `Friend` klíčového slova v oddílu deklarace třídy.  
  
- Chcete-li vytvořit konstantu dostupnou v celé aplikaci, deklarujte ji pomocí `Public` klíčového slova v oddílu deklarace třídy.  
  
 Další informace naleznete v tématu [How to: Declare a konstante](how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Zamezení cyklických odkazů  
 Vzhledem k tomu, že konstanty lze definovat v souvislosti s jinými konstantami, je možné neúmyslně vytvořit *cyklus*nebo cyklický odkaz mezi dvěma nebo více konstantami. K cyklu dochází, když máte dvě nebo více veřejných konstant, z nichž každá je definována z hlediska druhé, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 Pokud dojde k cyklu, Visual Basic vygeneruje chybu kompilátoru.  
  
## <a name="see-also"></a>Viz také

- [Const – příkaz](../../../language-reference/statements/const-statement.md)
- [Datové typy konstanty a literálu](constant-and-literal-data-types.md)
- [Konstanty a výčty](index.md)
- [Konstanty a výčty](../../../language-reference/constants-and-enumerations.md)
- [Přehled výčtů](enumerations-overview.md)
- [Přehled konstant](constants-overview.md)
- [Postupy: deklarace výčtu](how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
