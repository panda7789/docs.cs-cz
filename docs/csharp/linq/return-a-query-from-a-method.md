---
title: Vrácení dotazu z metody
description: Jak vrátit dotaz.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972512"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Jak vrátit dotaz z metody (C# Programovací průvodce)
Tento příklad ukazuje, jak vrátit dotaz z metody jako `out` vrácená hodnota a jako parametr.  
  
 Objekty dotazu jsou kompozitelné, což znamená, že můžete vrátit dotaz z metody. Objekty, které představují dotazy neukládají výsledné kolekce, ale spíše kroky k vytvoření výsledků v případě potřeby. Výhodou vrácení objektů dotazu z metod je, že mohou být dále složeny nebo změněny. Proto všechny vrácené hodnoty nebo `out` parametr metody, která vrací dotaz musí mít také tento typ. Pokud metoda zhmotní dotaz do <xref:System.Collections.Generic.List%601> konkrétní <xref:System.Array> nebo typ, je považován za vrácení výsledků dotazu namísto samotného dotazu. Proměnná dotazu, která je vrácena z metody, může být stále složena nebo změněna.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu první metoda vrátí dotaz jako vrácenou hodnotu a `out` druhá metoda vrátí dotaz jako parametr. Všimněte si, že v obou případech se jedná o dotaz, který je vrácen, nikoli výsledky dotazu.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
