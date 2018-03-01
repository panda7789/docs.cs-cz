---
title: 'Postupy: Deklarace konstanty (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 554f659e060087228fb43efd8b9d06103e21e980
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Postupy: Deklarace konstanty (Visual Basic)
Můžete použít `Const` příkaz deklarace konstanty a nastavení jeho hodnoty. Deklarováním konstanta, přiřaďte k hodnotě nějaký výstižný název. Jakmile je deklarovaná konstanta, nelze změnit ani přiřazena nová hodnota.  
  
 Můžete deklarace konstanty v rámci procedury nebo v části deklarace modulu, třídu nebo strukturu. Třída nebo konstanty na úrovni struktura `Private` ve výchozím nastavení, ale také může být deklarována jako `Public`, `Friend`, `Protected`, nebo `Protected Friend` pro příslušnou úroveň přístupu, kód.  
  
 Konstanty musí mít platný symbolický název (pravidla jsou stejné jako pro vytvoření názvy proměnných) a výrazu složený numeric nebo string konstanty a operátory (ale žádná volání funkce).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Chcete-li deklarace konstanty  
  
-   Zápis deklaraci, která zahrnuje specifikátor přístupu, `Const` – klíčové slovo a výraz, jako v následujících příkladech:  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     Když [Option Infer –](../../../../visual-basic/language-reference/statements/option-infer-statement.md) je `Off` a [možnost striktní](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, musí deklarovat konstantu explicitně zadáním datový typ (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, nebo `String`).  
  
     Když `Option Infer` je `On` nebo `Option Strict` je `Off`, můžou deklarovat konstanta bez zadání datový typ s `As` klauzule. Kompilátor Určuje typ konstanty z typu výraz. Další informace najdete v tématu [literálové datové typy a konstanta](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Chcete-li deklarovat konstanta, která má explicitně stanovené datový typ.  
  
-   Zápis deklaraci, která zahrnuje `As` – klíčové slovo a explicitního datového typu, jako v následujících příkladech:  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     Na jeden řádek, můžou deklarovat více konstanty, i když váš kód je lépe čitelný, pokud je deklarovat pouze jeden konstanta na každý řádek. Pokud je na jednom řádku deklarovat několik konstanty, se musí mít stejnou úroveň přístupu (`Public`, `Private`, `Friend`, `Protected`, nebo `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Deklarovat na jednom řádku více konstant  
  
-   Deklarací oddělte čárkou a mezerou, jako v následujícím příkladu:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Const – příkaz](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [Datové typy konstanty a literálu](constant-and-literal-data-types.md)  
 [Přehled konstant](constants-overview.md) [postupy: deklarace konstanty](how-to-declare-a-constant.md) [uživatelem definované konstanty](user-defined-constants.md) [datové typy konstanty a literálu](constant-and-literal-data-types.md) [postup: skupiny Souvisejících hodnot konstant](how-to-group-related-constant-values-together.md) [přehled výčtů](enumerations-overview.md) [postupy: deklarace výčtů](how-to-declare-enumerations.md) [postupy: odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md) [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md) [postupy: iterace výčet](how-to-iterate-through-an-enumeration.md) [postupy: určení řetězce spojeného s hodnotou výčtu](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Kdy použít výčet](when-to-use-an-enumeration.md)

 [Přehled výčtů](enumerations-overview.md)  
 [Přehled konstant](constants-overview.md)  
 [Postupy: deklarace výčtů](how-to-declare-enumerations.md)  
 [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)  
 [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
