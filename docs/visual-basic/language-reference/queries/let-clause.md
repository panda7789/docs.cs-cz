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
ms.openlocfilehash: 6484da5329c8240735b7c35f506637dd01cbeda4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604468"
---
# <a name="let-clause-visual-basic"></a>Let – klauzule (Visual Basic)
Vypočítá hodnotu a přiřadí ji k nové proměnné v dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`variable`|Požadováno. Alias, který slouží k odkazování výsledky zadaný výraz.|  
|`expression`|Požadováno. Výraz, který bude vyhodnocen a přiřazené k zadané proměnné.|  
  
## <a name="remarks"></a>Poznámky  
 `Let` Klauzule umožňuje výpočetní hodnoty pro každý výsledek dotazu a odkazujte na ně pomocí alias. Alias lze použít v jiných klauzulích, jako `Where` klauzule. `Let` Klauzule umožňuje vytvářet příkaz dotazu, který lze snadněji přečíst, protože můžete zadat alias pro klauzuli výraz, který je zahrnutý v dotazu a nahraďte alias pokaždé, když se používá v klauzuli výraz.  
  
 Může obsahovat libovolný počet `variable` a `expression` přiřazení v `Let` klauzule. Každé přiřazení oddělte čárkou (,).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Let` klauzule k výpočtu 10 procent slevy na produkty.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
