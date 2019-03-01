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
ms.openlocfilehash: 545eefc67d52428470c19b62085fd87927505c7e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972700"
---
# <a name="let-clause-visual-basic"></a>Let – klauzule (Visual Basic)
Vypočítá hodnotu a přiřadí ji nové proměnné v rámci dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`variable`|Povinný parametr. Alias, který slouží k odkazování výsledky poskytnutý výraz.|  
|`expression`|Povinný parametr. Výraz, který bude vyhodnocen a přiřazen k zadané proměnné.|  
  
## <a name="remarks"></a>Poznámky  
 `Let` Klauzule můžete k výpočtu hodnoty pro každý výsledek dotazu a na ně odkazovat pomocí alias. Alias je možné v jiných klauzulích, jako `Where` klauzuli. `Let` Klauzule vám umožní vytvořit příkaz dotazu, který je snazší přečíst, protože můžete zadat jako alias pro klauzuli výraz obsažena v dotazu a nahraďte aliasem, který se pokaždé, když se používá v klauzuli výrazu.  
  
 Může obsahovat libovolný počet `variable` a `expression` přiřazení v `Let` klauzuli. Každé přiřazení oddělte čárkou (,).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Let` klauzule compute 10 % slevu na produkty.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Viz také:
- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
