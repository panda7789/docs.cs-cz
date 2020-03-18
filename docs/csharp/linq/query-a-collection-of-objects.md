---
title: Dotaz na kolekci objektů (LINQ v c#)
description: Zjistěte, jak kolekce dotazů pomocí LINQ v C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659807"
---
# <a name="query-a-collection-of-objects"></a>Dotazování na kolekci objektů

Tento příklad ukazuje, jak provést jednoduchý `Student` dotaz přes seznam objektů. Každý `Student` objekt obsahuje některé základní informace o studentovi a seznam, který představuje skóre studenta na čtyřech zkouškách.  
  
Tato aplikace slouží jako rámec pro mnoho dalších příkladů `students` v této části, které používají stejný zdroj dat.  
  
## <a name="example"></a>Příklad

Následující dotaz vrátí studentům, kteří při první zkoušce obdrželi skóre 90 nebo vyšší.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
Tento dotaz je záměrně jednoduché, aby vám umožní experimentovat. Můžete například vyzkoušet další `where` podmínky v klauzuli nebo použít klauzuli `orderby` k řazení výsledků.  
  
## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
- [Interpolace řetězců](../language-reference/tokens/interpolated.md)
