---
title: Zpracování hodnot null ve výrazech dotazů
description: 'Postupy: zpracování hodnot null ve výrazech dotazů.'
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: ecd174462ef51a6dd7b7696abb9e111fc32d9ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272384"
---
# <a name="handle-null-values-in-query-expressions"></a>Zpracování hodnot null ve výrazech dotazů

Tento příklad ukazuje postup zpracování možných hodnot null ve zdrojové kolekce. Kolekci objektů, jako <xref:System.Collections.Generic.IEnumerable%601> může obsahovat elementy, jejichž hodnoty se [null](../language-reference/keywords/null.md). Pokud zdrojové kolekci je null nebo obsahuje element, jehož hodnota je null a dotaz nezpracovává hodnoty null, <xref:System.NullReferenceException> bude vyvolána při spuštění dotazu.  
  
## <a name="example"></a>Příklad

 Můžete obranu kódu předejdete výjimka odkazu s hodnotou null, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 V předchozím příkladu `where` klauzule odfiltruje všechny elementy null v pořadí kategorií. Tento postup je nezávislé na hodnotu null. Zkontrolujte v klauzuli join. Podmíněným výrazem s hodnotou null v tomto příkladu funguje, protože `Products.CategoryID` je typu `int?` což je sdružená vlastnost `Nullable<int>`.  
  
## <a name="example"></a>Příklad

 V klauzuli join-li jen jeden z klíčů porovnání je typ s možnou hodnotou Null hodnoty, můžete obsadit dalších na typ s možnou hodnotou Null ve výrazu dotazu. V následujícím příkladu předpokládáme, že `EmployeeID` je sloupec, který obsahuje hodnoty typu `int?`:  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Nullable%601>  
 [LINQ – výrazy dotazů](index.md)  
 [Typy s možnou hodnotou Null](../programming-guide/nullable-types/index.md)
