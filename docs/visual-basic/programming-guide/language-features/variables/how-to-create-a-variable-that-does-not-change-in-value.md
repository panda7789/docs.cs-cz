---
title: 'Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 7180e5141572d219ed02c57103e9d4b80cde536e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342931"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic)
Může zobrazit odporuje pojem proměnné, která se nezmění jeho hodnotu. Ale existují situace, kdy konstanty není možné vydat je a je užitečné mít proměnná s pevnou hodnotu. V takovém případě můžete členské proměnné s definovat [jen pro čtení](../../../../visual-basic/language-reference/modifiers/readonly.md) – klíčové slovo.  
  
 Nelze použít [Const příkaz](../../../../visual-basic/language-reference/statements/const-statement.md) k deklaraci a přiřazení konstantní hodnoty v následujících případech:  
  
-   `Const` Příkaz nepřijímá datový typ, který chcete použít  
  
-   Si nejste jisti hodnotu v době kompilace  
  
-   Nejde Vypočítat konstantní hodnotu v době kompilace  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>K vytvoření proměnné, která se nezmění na hodnotu  
  
1. Na úrovni modulu deklarace členské proměnné s [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)a zahrnout [jen pro čtení](../../../../visual-basic/language-reference/modifiers/readonly.md) – klíčové slovo.  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     Můžete zadat `ReadOnly` pouze na členské proměnné. To znamená, že je nutné definovat proměnné na úrovni modulu mimo všechny procedury.  
  
2. Pokud můžete vypočítat hodnotu v jediném příkazu v době kompilace, použijte klauzule inicializace v `Dim` příkazu. Postupujte podle [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule znaménko rovná se (`=`) a potom pomocí výrazu. Ujistěte se, že kompilátor můžete vyhodnotit tento výraz s konstantní hodnotou.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Můžete přiřadit hodnoty k `ReadOnly` proměnné pouze jednou. Až to uděláte tak, žádný kód někdy můžete změnit jeho hodnotu.  
  
     Pokud není známo, hodnota v době kompilace, nebo nelze vypočítat v době kompilace v jediném příkazu, stále ji můžete přiřadit v době běhu v konstruktoru. Chcete-li to provést, je třeba deklarovat `ReadOnly` proměnné na úrovni třídy nebo struktury. V konstruktoru třídy nebo struktury compute pevnou hodnotu proměnné a přiřadíte ho k proměnné návrat z konstruktoru.  
  
## <a name="see-also"></a>Viz také:

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md)
