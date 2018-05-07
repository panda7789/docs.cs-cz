---
title: Dotazování na kolekci objektů
description: Jak dotaz na kolekce.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: c690da2ae59d2a9b34a5bd403bc54797c4e95fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="query-a-collection-of-objects"></a>Dotazování na kolekci objektů
Tento příklad ukazuje, jak provést jednoduchý dotaz pro seznam `Student` objekty. Každý `Student` objekt obsahuje některé základní informace o student a seznam, který představuje Studentova skóre na čtyři kontroly.  
  
 Tato aplikace slouží jako rozhraní pro mnoho příklady v této části, které používají stejné `students` zdroj dat.  
  
## <a name="example"></a>Příklad  
 Následující dotaz vrátí studenty, kteří obdrželi skóre 90 nebo vyšší na jejich první zkoušku.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 Dotaz je umožnit experimentovat záměrně jednoduchá. Například můžete zkusit další podmínky v `where` klauzuli, nebo použijte `orderby` klauzule k řazení výsledků.  
  

## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)  
 [Interpolace řetězců](../language-reference/tokens/interpolated.md)
