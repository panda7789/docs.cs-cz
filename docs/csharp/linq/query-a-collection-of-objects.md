---
title: "Dotazování na kolekci objektů"
description: Jak dotaz na kolekce.
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 74d6c1f080c3e70867f5d2f074315bd1d8486bf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Interpolované řetězce](../language-reference/keywords/interpolated-strings.md)
