---
title: Základní datové typy
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: e85adb928925bf161e6e2d6ef935a20606f8eb32
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248027"
---
# <a name="basic-data-types"></a>Základní datové typy
Vzhledem k tomu, že se LINQ to SQL dotazy přeloží do jazyka Transact-SQL před jejich spuštěním na Microsoft SQL Server. LINQ to SQL podporuje většinu stejných integrovaných funkcí, které SQL Server používá pro základní datové typy.  
  
## <a name="casting"></a>Přetypování  
 Implicitní nebo explicitní přetypování jsou povolena ze zdrojového typu CLR do cílového typu CLR, pokud existuje podobný platný převod v rámci SQL Server. Další informace o přetypování CLR naleznete v tématu [funkce CType](../../../../../visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) a [operátory pro testování typů a přetypování](../../../../../csharp/language-reference/operators/type-testing-and-cast.md). Po převodu se přetypování mění chování operací provedených na výrazu CLR tak, aby odpovídaly chování jiných výrazů CLR, které jsou přirozeně mapovány na cílový typ. Přetypování je také možné přeložit v kontextu mapování dědičnosti. Objekty mohou být přetypování na konkrétnější podtypy entit tak, aby k nim bylo možné získávat data pro konkrétní podtypy.  
  
## <a name="equality-operators"></a>Operátory rovnosti  
 LINQ to SQL podporuje následující operátory rovnosti na základních datových typech v rámci LINQ to SQL dotazů:  
  
- Operátor rovnosti a nerovnosti: Operátory rovnosti a nerovnosti jsou podporovány pro typy <xref:System.Boolean>čísel <xref:System.DateTime>,, <xref:System.TimeSpan> a. Další informace o operátorech `=` Visual Basic `<>`a naleznete v tématu [operátory porovnání](../../../../../visual-basic/language-reference/operators/comparison-operators.md). C# Další informace o operátorech `==` porovnání a `!=`naleznete v tématu [operátory rovnosti](../../../../../csharp/language-reference/operators/equality-operators.md).
  
- Is – operátor: Při použití mapování dědičnosti má operátorpodporovanýpřeklad.`IS` Dá se použít místo přímého testování sloupce diskriminátoru k určení, zda je objekt určitého typu entity, a je přeložen na kontrolu sloupce diskriminátoru. Další informace o Visual Basic a C# jsou operátory, viz [operátor is](../../../../../visual-basic/language-reference/operators/is-operator.md) a [je](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator).  
  
## <a name="see-also"></a>Viz také:

- [Mapování typů SQL a CLR](sql-clr-type-mapping.md)
- [Datové typy a funkce](data-types-and-functions.md)
