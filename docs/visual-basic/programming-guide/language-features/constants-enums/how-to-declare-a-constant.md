---
title: 'Postupy: Deklarace konstanty (Visual Basic)'
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
ms.openlocfilehash: ce45e4df7f74cd68bde0fb2adba10197a11edb1b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394311"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Postupy: Deklarace konstanty (Visual Basic)
Můžete použít `Const` příkazu deklarace konstanty a nastavení jeho hodnoty. Deklarací konstantu, přiřaďte k hodnotě smysluplný název. Jakmile je deklarována konstanta, nelze změnit ani přiřazena nová hodnota.  
  
 Můžete deklarovat konstanty v rámci procedury nebo v části deklarace modulu, třídy nebo struktury. Třída nebo struktura úroveň konstanty jsou `Private` ve výchozím nastavení, ale může také deklarovány jako `Public`, `Friend`, `Protected`, nebo `Protected Friend` pro odpovídající úroveň přístup ke kódu.  
  
 Konstanty musí mít platný symbolický název (pravidla jsou stejné jako u vytváření názvy proměnných) a výraz složené číselné nebo řetězcové konstanty a operátory (ale bez volání funkce).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Chcete-li deklarovat konstanty  
  
-   Zápis deklarace, která zahrnuje specifikátor přístupu, `Const` – klíčové slovo a výraz, stejně jako v následujících příkladech:  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     Když [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) je `Off` a [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, musí deklarace konstanty explicitně tak, že zadáte datový typ (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, nebo `String`).  
  
     Když `Option Infer` je `On` nebo `Option Strict` je `Off`, je možné deklarovat konstanty bez zadání datový typ s `As` klauzuli. Kompilátor Určuje typ konstanty z typu výrazu. Další informace najdete v tématu [konstanty a literálu datové typy](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Chcete-li deklarovat konstantu, která je explicitně uvedená datový typ  
  
-   Zápis deklarace, která zahrnuje `As` – klíčové slovo a explicitního datového typu, stejně jako v následujících příkladech:  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     Na jednom řádku, může deklarovat více konstant, i když je váš kód lépe čitelný, je-li deklarovat jenom jednu konstantu na řádek. Je-li deklarovat více konstant na jednom řádku, musí všechny mají stejnou úroveň přístupu (`Public`, `Private`, `Friend`, `Protected`, nebo `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Chcete-li deklarovat více konstant na jednom řádku  
  
-   Deklarace oddělujte čárkou a mezerou, jako v následujícím příkladu:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [Datové typy konstanty a literálu](constant-and-literal-data-types.md)  
 [Přehled konstant](constants-overview.md) [postupy: deklarace konstanty](how-to-declare-a-constant.md) [uživatelem definované konstanty](user-defined-constants.md) [datové typy konstanty a literálu](constant-and-literal-data-types.md) [jak: skupina Souvisejících hodnot konstant](how-to-group-related-constant-values-together.md) [přehled výčtů](enumerations-overview.md) [postupy: deklarace výčtů](how-to-declare-enumerations.md) [postupy: odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md) [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md) [postupy: iterace ve výčtu](how-to-iterate-through-an-enumeration.md) [postupy: určení řetězce spojeného s hodnotou výčtu](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Kdy použít výčet](when-to-use-an-enumeration.md)

 [Přehled výčtů](enumerations-overview.md)  
 [Přehled konstant](constants-overview.md)  
 [Postupy: deklarace výčtů](how-to-declare-enumerations.md)  
 [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)  
 [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
