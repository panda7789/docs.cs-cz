---
title: 'Postupy: Vytvoření nové proměnné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: ee1e93b4e9819992f17738eb024004a4d66210d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938239"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Postupy: Vytvoření nové proměnné (Visual Basic)
Vytvořte proměnnou s [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Chcete-li vytvořit nové proměnné  
  
1. Deklarujte proměnnou v `Dim` příkazu.  
  
    ```  
    Dim newCustomer  
    ```  
  
2. Zahrnout specifikace vlastnosti proměnné, třeba [privátní](../../../../visual-basic/language-reference/modifiers/private.md), [statické](../../../../visual-basic/language-reference/modifiers/static.md), [stíny](../../../../visual-basic/language-reference/modifiers/shadows.md), nebo [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Další informace najdete v tématu [deklarované charakteristiky elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Není nutné `Dim` – klíčové slovo použití dalších klíčových slovech v deklaraci.  
  
3. Postupujte podle specifikace s názvem proměnné, které musí následovat Visual Basic – pravidla a pravidla týkající se. Další informace najdete v tématu [deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4. Postupujte podle názvu se [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule zadejte datový typ proměnné.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Pokud nezadáte datový typ, použije výchozí hodnota: `Object`.  
  
5. Postupujte podle `As` klauzule znaménko rovná se (`=`) a postupujte podle pokynů znaménka rovnosti s počáteční hodnotou proměnné.  
  
     Visual Basic přiřadí zadanou hodnotu k proměnné pokaždé, když ji spustí `Dim` příkazu. Pokud počáteční hodnotu nezadáte, Visual Basic přiřadí výchozí počáteční hodnotu pro datový typ proměnné, když poprvé vstoupí kód, který obsahuje `Dim` příkazu.  
  
     Pokud je proměnná typu odkazu, můžete vytvořit instanci její třídy zahrnutím [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo v `As` klauzuli. Pokud nepoužijete `New`, je počáteční hodnota proměnné [nic](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
