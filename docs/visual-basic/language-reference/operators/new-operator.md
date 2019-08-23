---
title: New – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955880"
---
# <a name="new-operator-visual-basic"></a>New – operátor (Visual Basic)
Zavádí klauzuli pro vytvoření nové instance objektu, určuje omezení konstruktoru pro parametr typu nebo `Sub` identifikuje proceduru jako konstruktor třídy. `New`  
  
## <a name="remarks"></a>Poznámky  
 V deklaraci nebo příkazu `New` přiřazení musí klauzule určovat definovanou třídu, ze které lze instanci vytvořit. To znamená, že třída musí vystavit jeden nebo více konstruktorů, ke kterým může přistupovat volající kód.  
  
 Můžete použít `New` klauzuli v příkazu deklarace nebo v příkazu přiřazení. Při spuštění příkazu volá příslušný konstruktor zadané třídy a předává všechny argumenty, které jste zadali. Následující příklad ukazuje to vytvořením instancí `Customer` třídy, která má dva konstruktory, jeden, který přebírá žádné parametry a jeden, který přijímá řetězcový parametr.  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 Vzhledem k tomu, že `New` pole jsou třídy, může vytvořit novou instanci pole, jak je znázorněno v následujících příkladech.  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 Modul CLR (Common Language Runtime) vyvolá <xref:System.OutOfMemoryException> chybu, pokud není k dispozici dostatek paměti pro vytvoření nové instance.  
  
> [!NOTE]
> `New` Klíčové slovo se používá také v seznamech parametrů typu k určení toho, že zadaný typ musí vystavit přístupný konstruktor bez parametrů. Další informace o parametrech typu a omezeních najdete v tématu [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Chcete-li vytvořit proceduru konstruktoru pro třídu, nastavte název `Sub` procedury `New` na klíčové slovo. Další informace najdete v tématu [životnost objektu: Způsob vytváření a zničení](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)objektů.  
  
 `New` Klíčové slovo lze použít v těchto kontextech:  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Tohoto](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.OutOfMemoryException>
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Doba života objektu: Vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
