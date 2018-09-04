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
ms.openlocfilehash: 34c0fd239d9e08dab4a107cb8447941e7ab3ecbe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516760"
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
|`variable`|Požadováno. Alias, který slouží k odkazování výsledky poskytnutý výraz.|  
|`expression`|Požadováno. Výraz, který bude vyhodnocen a přiřazen k zadané proměnné.|  
  
## <a name="remarks"></a>Poznámky  
 `Let` Klauzule můžete k výpočtu hodnoty pro každý výsledek dotazu a na ně odkazovat pomocí alias. Alias je možné v jiných klauzulích, jako `Where` klauzuli. `Let` Klauzule vám umožní vytvořit příkaz dotazu, který je snazší přečíst, protože můžete zadat jako alias pro klauzuli výraz obsažena v dotazu a nahraďte aliasem, který se pokaždé, když se používá v klauzuli výrazu.  
  
 Může obsahovat libovolný počet `variable` a `expression` přiřazení v `Let` klauzuli. Každé přiřazení oddělte čárkou (,).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Let` klauzule compute 10 % slevu na produkty.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/index.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
