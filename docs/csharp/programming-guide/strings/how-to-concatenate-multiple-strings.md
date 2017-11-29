---
title: "Postupy: Řetězení více řetězců (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a>Postupy: Řetězení více řetězců (Průvodce programováním v C#)
*Zřetězení* je proces připojování jeden řetězec na konec jiným řetězcem. Když pomocí zřetězení textové literály nebo řetězcové konstanty `+` operátor, kompilátor vytvoří jeden řetězec. Ne spustit, když dojde k zřetězení. Řetězec proměnné však může být zřetězen pouze za běhu. V takovém případě byste měli porozumět vliv na výkon různých přístupů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak rozdělit literálu dlouhý řetězec na menší řetězců za účelem zlepšení čitelnosti ve zdrojovém kódu. Tyto části bude zřetězen do jednoho řetězce v době kompilace. Už běží čas výkon, bez ohledu na počet řetězce související se situací.  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a>Příklad  
 Ke zřetězení proměnné řetězce, můžete použít `+` nebo `+=` operátory, nebo <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody. `+` Operátor se snadno používá a zajišťuje intuitivní kódu. I když používáte několik + operátory v jednom příkazu, obsah řetězce zkopírován pouze jednou. Pokud tuto operaci opakovat několikrát, například ve smyčce, může ale způsobit efektivitu problémy. Například vezměte na vědomí následující kód:  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  V operace s řetězci zřetězení kompilátor jazyka C# zpracovává řetězec null stejné jako prázdný řetězec, ale nepřevede hodnota řetězce původní hodnotu null.  
  
 Pokud nejsou zřetězení velkého počtu řetězce (například ve smyčce), náklady na výkon tohoto kódu je pravděpodobně není důležité. Totéž platí pro <xref:System.String.Concat%2A?displayProperty=nameWithType> a <xref:System.String.Format%2A?displayProperty=nameWithType> metody.  
  
 Ale pokud výkonu je důležité, byste měli vždycky používat <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců. Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců bez řetězení účinku `+` operátor.  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)
