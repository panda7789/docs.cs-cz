---
title: 'Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d63c254abe6d12c094e0d1252c9721f668947f09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651373"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic).
Znalost problematicky proměnné, která se nezmění jeho hodnota může vypadat jako odporuje. Ale existují situace, když konstanta není vhodná, a je užitečné používat proměnné s pevnou hodnotou. V takovém případě můžete definovat členské proměnné s [jen pro čtení](../../../../visual-basic/language-reference/modifiers/readonly.md) – klíčové slovo.  
  
 Nelze použít [příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md) deklarovat a přiřadit konstantní hodnotu v následujících případech:  
  
-   `Const` Příkaz nepřijímá datový typ, který chcete použít  
  
-   Neznáte hodnota v době kompilace  
  
-   Nelze vypočítat hodnotu konstanty v době kompilace  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>K vytvoření proměnné, která se nezmění na hodnotu  
  
1.  Na úrovni modulu deklarovat členské proměnné s [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)a zahrnout [jen pro čtení](../../../../visual-basic/language-reference/modifiers/readonly.md) – klíčové slovo.  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     Můžete zadat `ReadOnly` pouze na členské proměnné. To znamená, že je nutné definovat proměnnou na úrovni modulu mimo jakéhokoli postupu.  
  
2.  Pokud hodnota v jediném příkazu v době kompilace můžete vypočítat, použijte klauzuli inicializace v `Dim` příkaz. Postupujte podle [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule symbol rovná se (`=`), za nímž následují výrazu. Ujistěte se, že kompilátor můžete vyhodnotit na konstantní hodnotu výrazu.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Můžete přiřadit hodnotu na `ReadOnly` proměnné pouze jednou. Až to uděláte tak, žádný kód někdy změnit jeho hodnotu.  
  
     Pokud neznáte hodnotu v době kompilace, nebo nelze výpočetní v době kompilace v jediném příkazu, můžete ho přiřadit stále za běhu v konstruktoru. K tomu je potřeba deklarovat `ReadOnly` proměnné na úrovni třídu nebo strukturu. V konstruktoru pro tuto třídu nebo strukturu výpočetní pevná hodnota proměnné a přiřaďte ho do proměnné před vrácením z konstruktoru.  
  
## <a name="see-also"></a>Viz také  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md)
