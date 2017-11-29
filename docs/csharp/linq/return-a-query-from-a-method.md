---
title: "Vrácení dotazu z metody"
description: "Postup vrácení dotazu."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Postupy: Vrácení dotazu z metody (Průvodce programováním v C#)
Tento příklad ukazuje, jak jako návratová hodnota a jako vrácení dotazu z metody `out` parametr.  
  
 Objekty dotazu jsou složení, což znamená, že se můžete vrátit dotazu z metody. Objekty, které představují dotazy neukládejte výsledné kolekce, ale spíš kroky nepřineslo výsledky v případě potřeby. Výhodou vrácení objekty dotazu z metody je, aby mohly být další sestavit a upravit. Proto všechny návratové hodnoty nebo `out` parametru metody, která vrací dotaz musí také mít typu. Pokud bude metodu realizována dotazu do konkrétní <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> typu, považuje vracejí výsledky dotazu místo samotný dotaz. Proměnné dotazu, která je vrácena z metody můžete stále složené nebo upravil.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, první metoda vrací dotaz jako typ návratové hodnoty, a druhá metoda vrací dotaz jako `out` parametr. Všimněte si, že v obou případech je dotaz, který se vrátí, nebyl výsledky dotazu.  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)
