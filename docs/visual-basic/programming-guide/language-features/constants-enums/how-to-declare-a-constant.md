---
title: 'Postupy: Deklarace konstanty'
ms.date: 07/20/2015
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
ms.openlocfilehash: ffaa98f6af3d4b276f5c0b1153841acdea0809d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414476"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Postupy: Deklarace konstanty (Visual Basic)
Použijete `Const` příkaz k deklaraci konstanty a nastavení její hodnoty. Deklarováním konstanty přiřadíte smysluplný název k hodnotě. Jakmile je konstanta deklarována, nelze ji změnit ani jí přiřadit novou hodnotu.  
  
 Deklarujete konstantu v rámci procedury nebo v oddílu deklarace modulu, třídy nebo struktury. Konstanty na úrovni třídy nebo struktury jsou `Private` ve výchozím nastavení, ale mohou být také deklarovány jako `Public` ,, `Friend` `Protected` nebo `Protected Friend` pro příslušnou úroveň přístupu kódu.  
  
 Konstanta musí mít platný symbolický název (pravidla jsou stejná jako pro vytváření názvů proměnných) a výraz tvořený číselnými nebo řetězcovými konstantami a operátory (ale žádné volání funkcí).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Deklarace konstanty  
  
- Napište deklaraci, která zahrnuje specifikátor přístupu, `Const` klíčové slovo a výraz, jako v následujících příkladech:  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     Pokud je [možnost odvozená](../../../language-reference/statements/option-infer-statement.md) `Off` a [možnost Option Strict](../../../language-reference/statements/option-strict-statement.md) `On` , je nutné explicitně deklarovat konstantu zadáním datového typu ( `Boolean` , `Byte` , `Char` , `DateTime` , `Decimal` , `Double` , `Integer` , `Long` , `Short` , `Single` nebo `String` ).  
  
     Když `Option Infer` je `On` nebo `Option Strict` `Off` , můžete deklarovat konstantu bez zadání datového typu s `As` klauzulí. Kompilátor určuje typ konstanty z typu výrazu. Další informace naleznete v tématu [datové typy konstanty a literálu](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Deklarace konstanty, která má explicitně uvedený datový typ  
  
- Napište deklaraci, která zahrnuje `As` klíčové slovo a explicitní datový typ, jako v následujících příkladech:  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     Můžete deklarovat více konstant na jednom řádku, i když je váš kód čitelnější, pokud deklarujete pouze jednu konstantu na řádek. Pokud deklarujete více konstant na jednom řádku, musí mít všechny stejnou úroveň přístupu ( `Public` , `Private` ,, `Friend` `Protected` nebo `Protected Friend` ).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Deklarace více konstant na jednom řádku  
  
- Deklarace se oddělují čárkou a mezerou, jako v následujícím příkladu:  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Viz také

- [Const – příkaz](../../../language-reference/statements/const-statement.md)
- [Datové typy konstanty a literálu](constant-and-literal-data-types.md)
- [Přehled konstant](constants-overview.md)
- [Postupy: Deklarace konstanty](how-to-declare-a-constant.md)
- [Uživatelem definované konstanty](user-defined-constants.md)
- [Datové typy konstanty a literálu](constant-and-literal-data-types.md)
- [Postupy: Seskupení souvisejících hodnot konstant](how-to-group-related-constant-values-together.md)
- [Přehled výčtů](enumerations-overview.md)
- [Postupy: Deklarace výčtů](how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Postupy: Iterace ve výčtu](how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](when-to-use-an-enumeration.md)

- [Přehled výčtů](enumerations-overview.md)
- [Přehled konstant](constants-overview.md)
- [Postupy: deklarace výčtu](how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
- [Konstanty a výčty](../../../language-reference/constants-and-enumerations.md)
