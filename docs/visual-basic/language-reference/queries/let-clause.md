---
title: Let – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004726"
---
# <a name="let-clause-visual-basic"></a>Let – klauzule (Visual Basic)
Vypočítá hodnotu a přiřadí ji k nové proměnné v rámci dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`variable`|Požadováno. Alias, který lze použít k odkazování na výsledky poskytnutého výrazu.|  
|`expression`|Požadováno. Výraz, který bude vyhodnocen a přiřazen k zadané proměnné.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Let` umožňuje vypočítat hodnoty pro každý výsledek dotazu a odkazovat na ně pomocí aliasu. Alias lze použít v jiných klauzulích, například v klauzuli `Where`. Klauzule `Let` umožňuje vytvořit příkaz dotazu, který je snazší číst, protože můžete zadat alias pro klauzuli Expression, který je součástí dotazu, a nahradit alias pokaždé, když se použije klauzule Expression.  
  
 V klauzuli `Let` můžete zahrnout libovolný počet přiřazení `variable` a `expression`. Jednotlivá přiřazení oddělte čárkou (,).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá klauzuli `Let` pro výpočet 10% slevy na produkty.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
