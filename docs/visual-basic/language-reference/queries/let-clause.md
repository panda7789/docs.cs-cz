---
title: "Let – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70e47517a62f58dcababd31c26277417b62eab66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Kde – klauzule](../../../visual-basic/language-reference/queries/where-clause.md)
