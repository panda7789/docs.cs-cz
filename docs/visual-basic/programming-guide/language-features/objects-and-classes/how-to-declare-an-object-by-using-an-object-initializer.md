---
title: 'Postupy: Deklarace objektu pomocí inicializátoru objektu'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: cf4954059a4b0bf015bed82a74357ecfd5f5987e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404872"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)
Inicializátory objektů umožňují deklarovat a vytvořit instanci instance třídy v jednom příkazu. Kromě toho můžete inicializovat jednoho nebo více členů instance současně bez vyvolání parametrizovaného konstruktoru.  
  
 Použijete-li inicializátor objektu k vytvoření instance pojmenovaného typu, je volán konstruktor bez parametrů pro třídu, následovaný inicializací zadaných členů v pořadí, které zadáte.  
  
 Následující postup ukazuje, jak vytvořit instanci `Student` třídy třemi různými způsoby. Třída má jako křestní jméno, příjmení a vlastnosti roku třídy mezi ostatními. Každá ze tří deklarací vytvoří novou instanci třídy `Student` s vlastností `First` nastavenou na "Michael", vlastnost `Last` nastavenou na "Tucker" a všechny ostatní členy nastavené na výchozí hodnoty. Výsledek každé deklarace v proceduře je ekvivalentní následujícímu příkladu, který nepoužívá inicializátor objektu.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Implementaci `Student` třídy naleznete v tématu [How to: Create a list of Items](../../concepts/linq/how-to-create-a-list-of-items.md). Můžete zkopírovat kód z tohoto tématu a nastavit třídu a vytvořit seznam `Student` objektů, se kterými chcete pracovat.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Vytvoření objektu pojmenované třídy pomocí inicializátoru objektu  
  
1. Zahajte deklaraci, jako kdybyste naplánovali použití konstruktoru.  
  
     `Dim student1 As New Student`  
  
2. Zadejte klíčové slovo `With` následovaný inicializačním seznamem ve složených závorkách.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. V inicializačním seznamu Zahrňte všechny vlastnosti, které chcete inicializovat, a přiřaďte k ní počáteční hodnotu. Před název vlastnosti je uvedena tečka.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Můžete inicializovat jednoho nebo více členů třídy.  
  
4. Alternativně můžete deklarovat novou instanci třídy a pak jí přiřadit hodnotu. Nejdřív deklarujte instanci `Student` :  
  
     `Dim student2 As Student`  
  
5. Začněte vytvářet instanci `Student` normálním způsobem.  
  
     `Dim student2 As Student = New Student`  
  
6. Zadejte `With` a pak inicializátor objektu pro inicializaci jednoho nebo více členů nové instance.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Definici v předchozím kroku můžete zjednodušit tím, že ji vynecháte `As Student` . Pokud to uděláte, kompilátor určí, že `student3` je instancí aplikace `Student` pomocí odvození místního typu.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Další informace naleznete v tématu [odvození místního typu](../variables/local-type-inference.md).  
  
## <a name="see-also"></a>Viz také

- [Odvození místního typu](../variables/local-type-inference.md)
- [Postupy: Vytvoření seznamu položek](../../concepts/linq/how-to-create-a-list-of-items.md)
- [Inicializátory objektů: pojmenované a anonymní typy](object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](anonymous-types.md)
