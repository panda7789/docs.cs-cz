---
title: "Skip While – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a>Skip While – klauzule (Visual Basic)
Obchází elementů v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který představuje podmínku, kterou chcete testovat prvky pro. Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, například `Integer` má být vyhodnocen jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 `Skip While` Klauzule obchází elementy od začátku až do zadaných výsledků dotazu `expression` vrátí `false`. Po `expression` vrátí `false`, dotaz vrátí všechny zbývající elementy. `expression` Pro zbývající výsledky se ignoruje.  
  
 `Skip While` Klauzule se liší od `Where` klauzule v tom, že `Where` klauzuli lze použít k vyloučení všechny elementy z dotazu, které nesplňují určité podmínky. `Skip While` Klauzule vyloučí elementy pouze dokud poprvé, která není splněna podmínka. `Skip While` Klauzule je nejvhodnější pro práci se výsledek seřazené dotazu.  
  
 Můžete obejít konkrétní počet výsledků od začátku výsledků dotazu pomocí `Skip` klauzule.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Skip While` klauzule obejít výsledky, dokud nebude nalezen první zákazník z USA.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Skip – klauzule](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take While – klauzule](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Kde – klauzule](../../../visual-basic/language-reference/queries/where-clause.md)
