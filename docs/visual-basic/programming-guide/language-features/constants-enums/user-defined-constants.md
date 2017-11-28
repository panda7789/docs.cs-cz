---
title: "Uživatelem definované konstanty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce839c3e843a52b31e40c13cb765f8eaf9959ea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-constants-visual-basic"></a>Uživatelem definované konstanty (Visual Basic)
Konstanta je smysluplný název, který probíhá číslo nebo řetězec, který se nemění. Konstanty ukládat hodnoty, které jak již název napovídá, zůstat konstantní po spuštění aplikace. Můžete použít konstanty, které jsou definovány pro ovládací prvky nebo součásti, se kterými můžete pracovat, nebo můžete vytvořit vlastní. Konstanty vytvořit sami jsou popsány jako *uživatelem definované*.  
  
 Deklarace konstanty s `Const` příkaz, pomocí stejné pokyny byste pro vytvoření název proměnné. Pokud `Option Strict` je `On`, je potřeba explicitně deklarovat typu konstanty.  
  
## <a name="const-statement-usage"></a>Const – příkaz využití  
 A `Const` příkaz může představovat matematické nebo datum a čas množství:  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 Je také definovat `String` konstanty:  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 Výraz na pravé straně znaménkem rovnosti ( `=` ) je často číslo nebo řetězcového literálu, ale také může být výraz, který je výsledkem číslo nebo řetězec (i když tento výraz nemůže obsahovat volání funkcí). Můžete definovat i konstanty z hlediska dříve definované konstanty:  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>Rozsah uživatelem definované konstanty  
 A `Const` oboru na příkazu je stejný jako u proměnná definovaná ve stejném umístění. Můžete určit obor v některém z následujících způsobů:  
  
-   Pokud chcete vytvořit konstanta, která existuje pouze v rámci procedury, deklarujte ji v rámci tohoto postupu.  
  
-   K vytvoření k dispozici všechny postupy v rámci třídy, ale není žádný kód mimo tento modul konstanta, deklarujte v sekci deklarace třídy.  
  
-   Pokud chcete vytvořit konstanta, která je k dispozici pro všechny členy sestavení, ale ne mimo klientům sestavení, deklarujte ji pomocí `Friend` – klíčové slovo v sekci deklarace třídy.  
  
-   K vytvoření k dispozici v celé aplikaci konstanta, deklarujte ji pomocí `Public` – klíčové slovo v prohlášeních části třídy.  
  
 Další informace najdete v tématu [postupy: deklarace konstanty A](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Zamezení cyklické odkazy  
 Protože konstanty mohou být definovány jako ostatní konstanty, je možné nechtěně vytvořit *cyklus*, nebo cyklický odkaz mezi dva nebo více konstanty. Cyklus dojde, pokud máte dva nebo víc veřejných konstanty, z nichž každý je definována v jiné, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Pokud dojde k cyklus, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generuje chybu kompilátoru.  
  
## <a name="see-also"></a>Viz také  
 [Const – příkaz](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Konstanty a výčty](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
