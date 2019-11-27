---
title: Operátor new
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
ms.openlocfilehash: 27b5b4516ef729045036c36fedc24b6c576a4f61
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348321"
---
# <a name="new-operator-visual-basic"></a>New – operátor (Visual Basic)

Zavádí klauzuli `New` pro vytvoření nové instance objektu, určuje omezení konstruktoru pro parametr typu nebo identifikuje `Sub` proceduru jako konstruktor třídy.

## <a name="remarks"></a>Poznámky

V deklaraci nebo příkazu přiřazení musí klauzule `New` určovat definovanou třídu, ze které lze instanci vytvořit. To znamená, že třída musí vystavit jeden nebo více konstruktorů, ke kterým může přistupovat volající kód.

V příkazu deklarace nebo příkazu přiřazení můžete použít klauzuli `New`. Při spuštění příkazu volá příslušný konstruktor zadané třídy a předává všechny argumenty, které jste zadali. Následující příklad ukazuje to vytvořením instancí třídy `Customer`, která má dva konstruktory, jeden, který přebírá žádné parametry a jeden, který přijímá řetězcový parametr:

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

Vzhledem k tomu, že pole jsou třídy, `New` mohou vytvořit novou instanci pole, jak je znázorněno v následujícím příkladu:

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

Modul CLR (Common Language Runtime) vyvolá chybu <xref:System.OutOfMemoryException>, pokud není k dispozici dostatek paměti pro vytvoření nové instance.

> [!NOTE]
> Klíčové slovo `New` se používá také v seznamech parametrů typu k určení toho, že zadaný typ musí vystavit přístupný konstruktor bez parametrů. Další informace o parametrech typu a omezeních najdete v tématu [seznam typů](../statements/type-list.md).

Chcete-li vytvořit proceduru konstruktoru pro třídu, nastavte název `Sub` procedury na klíčové slovo `New`. Další informace naleznete v tématu [Doba života objektu: vytváření a zničení objektů](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

Klíčové slovo `New` lze použít v těchto kontextech:

- [Příkaz Dim](../statements/dim-statement.md)
- [Tohoto](../statements/of-clause.md)
- [Příkaz Sub](../statements/sub-statement.md)

## <a name="see-also"></a>Viz také:

- <xref:System.OutOfMemoryException>
- [Klíčová slova](../keywords/index.md)
- [Seznam typů](../statements/type-list.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Doba života objektu: Vytváření a zničení objektů](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
