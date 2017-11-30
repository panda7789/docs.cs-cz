---
title: "Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c818765cbeac7a3080ee666d464052493e5bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)
Inicializátory objektů umožňují deklarace a vytvoří instanci třídy v jediném příkazu. Navíc můžete inicializovat jednoho nebo více členů instance ve stejnou dobu, bez vyvolání parametrizované konstruktor.  
  
 Při vytvoření instance typu s názvem pomocí inicializátoru objektu, se nazývá výchozí konstruktor pro třídu, za nímž následuje inicializace určené členů v pořadí, ve kterém zadáte.  
  
 Následující postup ukazuje, jak vytvořit instanci `Student` třída třemi různými způsoby. Třída nemá křestní jméno, příjmení a vlastnosti třídy roku, mimo jiné. Všechny tři deklarace vytvoří novou instanci třídy `Student`, s vlastností `First` nastavena na "Michael", vlastnost `Last` nastavený na "Tucker", a všechny ostatní členy na výchozí hodnoty. Výsledek každé deklarace v postupu je ekvivalentní v následujícím příkladu, který nepoužívá inicializátoru objektu.  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 Implementace `Student` třídy najdete v tématu [postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Můžete zkopírovat kód z tohoto tématu nastavit třídy a vytvoří seznam `Student` objekty, které chcete pracovat.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Chcete-li vytvořit objekt s názvem třídy pomocí inicializátoru objektu  
  
1.  Začněte deklaraci, jako když plánujete použít konstruktor.  
  
     `Dim student1 As New Student`  
  
2.  Zadejte klíčové slovo `With`, za nímž následují seznamu k inicializaci složené závorky.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  V seznamu inicializace zahrňte každou vlastnost, kterou chcete inicializovat a přiřadit výchozí hodnoty. Název vlastnosti je začínat tečkou.  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     Jeden nebo více členů třídy můžete inicializovat.  
  
4.  Alternativně můžete deklarovat novou instanci třídy a pak do ní přiřadit hodnotu. Nejprve deklarujte instanci `Student`:  
  
     `Dim student2 As Student`  
  
5.  Zahájit vytvoření instance `Student` běžným způsobem.  
  
     `Dim student2 As Student = New Student`  
  
6.  Typ `With` a pak inicializátoru objektu k inicializaci nové instance jednoho nebo více členů.  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  Definice v předchozím kroku můžete zjednodušit tím vynechání `As Student`. Pokud to uděláte, kompilátor zjistí, `student3` je instance `Student` pomocí odvození místního typu.  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Viz také  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
