---
title: Dotazování na kolekci objektů (LINQ v JAZYKU C#)
description: Zjistěte, jak dát dotaz na kolekce pomocí jazyka LINQ v jazyce C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 7bc59e7009f9ae8d8f66c24e9519d9100404c9c4
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256139"
---
# <a name="query-a-collection-of-objects"></a>Dotazování na kolekci objektů

Tento příklad ukazuje, jak provést jednoduchý dotaz přes seznam `Student` objekty. Každý `Student` objekt obsahuje některé základní informace o studenta a seznam, který představuje student získal skóre na čtyři zkoušky.  
  
Tato aplikace slouží jako architektura pro mnoho příkladů v této části, které používají stejné `students` zdroj.  
  
## <a name="example"></a>Příklad

Následující dotaz vrátí studenty, kteří obdrželi skóre 90 nebo vyšší na jejich první zkoušku.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
Tento dotaz je záměrně jednoduchá umožňují snadno experimentovat. Například můžete vyzkoušet další podmínky v `where` klauzuli, nebo použijte `orderby` klauzule řazení výsledků.  
  
## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)  
- [Interpolace řetězců](../language-reference/tokens/interpolated.md)