---
title: 'Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 775c40cbb62272f913297d5a58914a0c82c5a7d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780832"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)
Inicializátory objektů umožňují deklarovat a vytvoří instanci třídy v jediném příkazu. Kromě toho můžete inicializovat jednoho nebo více členů instance ve stejnou dobu bez vyvolání konstruktoru s parametry.  
  
 Použijete-li vytvořit instanci typu s názvem inicializátoru objektu, je zavolán výchozí konstruktor pro třídu, za nímž následuje inicializace členů určené ve vámi určeném pořadí.  
  
 Následující postup ukazuje, jak vytvořit instanci `Student` třídy třemi různými způsoby. Třída má křestní jméno, příjmení a vlastnosti třídy rok, mimo jiné. Všechny tři deklarace vytvoří novou instanci třídy `Student`, s vlastností `First` nastavena na "Michael", vlastnost `Last` nastavená na "Tucker" a všechny ostatní členové nastavená na výchozí hodnoty. Výsledek deklaraci v postupu je ekvivalentní v následujícím příkladu, který nepoužívá inicializátoru objektu.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Pro implementaci `Student` najdete v tématu [jak: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Můžete zkopírovat kód z tohoto tématu nastavit třídy a vytvořit seznam `Student` pro práci s objekty.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Chcete-li vytvořit objekt s názvem třídy pomocí inicializátoru objektů  
  
1. Začněte deklarace, jako kdyby jste naplánovali použijte konstruktor.  
  
     `Dim student1 As New Student`  
  
2. Klíčové slovo `With`následovaný inicializačního seznamu ve složených závorkách.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. V seznamu inicializace zahrňte každou vlastnost, kterou chcete inicializovat a přiřadit je počáteční hodnota. Název vlastnosti je začínat tečkou.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Můžete inicializovat jednoho nebo více členů třídy.  
  
4. Alternativně můžete deklarovat novou instanci třídy a pak do něj přiřadit hodnotu. Nejprve deklarujte instanci `Student`:  
  
     `Dim student2 As Student`  
  
5. Zahájit vytvoření instance `Student` běžným způsobem.  
  
     `Dim student2 As Student = New Student`  
  
6. Typ `With` a potom inicializátoru objektu inicializovat jednoho nebo více členů nové instance.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Definice v předchozím kroku může zjednodušit vynecháním `As Student`. Pokud to uděláte, kompilátor zjistí, že `student3` je instance `Student` pomocí odvození místního typu.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Viz také:

- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Postupy: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
