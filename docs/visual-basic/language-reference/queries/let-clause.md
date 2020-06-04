---
title: Let – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 4bf832651d9753c41ee5a02defec4adc55af1ff1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359758"
---
# <a name="let-clause-visual-basic"></a>Let – klauzule (Visual Basic)
Vypočítá hodnotu a přiřadí ji k nové proměnné v rámci dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`variable`|Povinná hodnota. Alias, který lze použít k odkazování na výsledky poskytnutého výrazu.|  
|`expression`|Povinná hodnota. Výraz, který bude vyhodnocen a přiřazen k zadané proměnné.|  
  
## <a name="remarks"></a>Poznámky  
 `Let`Klauzule umožňuje vypočítat hodnoty pro každý výsledek dotazu a odkazovat na ně pomocí aliasu. Alias lze použít v jiných klauzulích, jako je například `Where` klauzule. `Let`Klauzule umožňuje vytvořit příkaz dotazu, který je snazší číst, protože můžete zadat alias klauzule Expression, který je součástí dotazu, a nahradit alias pokaždé, když se použije klauzule Expression.  
  
 V klauzuli můžete zadat libovolný počet `variable` a `expression` přiřazení `Let` . Jednotlivá přiřazení oddělte čárkou (,).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Let` klauzuli pro výpočet 10% slevy na produkty.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Klauzule WHERE](where-clause.md)
