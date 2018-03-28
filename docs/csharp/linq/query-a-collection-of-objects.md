---
title: Dotazování na kolekci objektů
description: Jak dotaz na kolekce.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: a62e5c6324d15376f1b42ad078eeb883b05ef14f
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
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
