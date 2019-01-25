---
title: Základní datové typy
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: d9c79ae70d860c5e86d4338038b3158ebfba184f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704966"
---
# <a name="basic-data-types"></a>Základní datové typy
Protože dotazech LINQ to SQL přeložit do jazyka Transact-SQL před jsou prováděna na serveru Microsoft SQL Server. Technologie LINQ to SQL podporuje velkou část stejné vestavěné funkce systému SQL Server nemá pro základní datové typy.  
  
## <a name="casting"></a>Přetypování  
 Implicitní nebo explicitní přetypování jsou povolené ze zdroje typu CLR pro cílový typ CLR Pokud podobně jako platnou konverzi v rámci SQL serveru. Další informace o přetypování CLR naleznete v tématu [funkce CType](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) a [jako](~/docs/csharp/language-reference/keywords/as.md). Po převodu přetypování změnit chování operace provedené na výrazu CLR tak, aby odpovídaly chování dalších výrazů CLR, které přirozeně mapovat na typ cíle. Použití přetypování je také Přeložitelné v rámci mapování dědičnosti. Objekty lze přetypovat na konkrétnější podtypy entity, tak, aby jejich podtyp konkrétní data přístupná.  
  
## <a name="equality-operators"></a>Operátory rovnosti  
 Technologie LINQ to SQL podporuje následující operátory rovnosti na základní datové typy v LINQ dotazy SQL:  
  
-   Stejné a operátor nerovnosti: Operátory rovnosti a nerovnosti jsou podporovány pro numerické <xref:System.Boolean>, <xref:System.DateTime>, a <xref:System.TimeSpan> typy. Další informace o tom operátory jazyka Visual Basic `=` a `<>`, naleznete v tématu [operátory porovnání](~/docs/visual-basic/language-reference/operators/comparison-operators.md). Další informace o C# operátory porovnání `==` a `!=`, naleznete v tématu [== – operátor](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) a [! = – operátor](~/docs/csharp/language-reference/operators/not-equal-operator.md)v uvedeném pořadí  
  
-   Je operátor: `IS` Při mapování dědičnosti má operátor podporovaných překladů. Lze použít místo přímo testování sloupec diskriminátoru a určí, zda objekt typu konkrétní entity, je přeložen na kontrolu sloupec diskriminátoru. Další informace o jazyce Visual Basic a C# je operátory, naleznete v tématu [je operátor](~/docs/visual-basic/language-reference/operators/is-operator.md) a [je](~/docs/csharp/language-reference/keywords/is.md).  
  
## <a name="see-also"></a>Viz také:
- [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
