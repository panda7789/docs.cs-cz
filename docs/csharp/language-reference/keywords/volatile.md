---
title: "volatile (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords: volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cefa39313c3c551e8d05fbc31e528b86c6888d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="volatile-c-reference"></a>volatile (Referenční dokumentace jazyka C#)
`volatile` – Klíčové slovo označuje, že pole mohou být změněna více vláken, které jsou prováděny ve stejnou dobu. Pole, které jsou deklarovány `volatile` nevztahují kompilátoru optimalizace, které předpokládá přístup podle jednoho vlákna. Tím se zajistí, že aktuální hodnota je přítomen v poli za všech okolností.  
  
 `volatile` Modifikátor se obvykle používá pro pole, kterému je získat přístup z více vláken bez použití [zámku](../../../csharp/language-reference/keywords/lock-statement.md) příkaz k serializaci přístup.  
  
 `volatile` – Klíčové slovo lze použít pro pole těchto typů:  
  
-   Odkazové typy.  
  
-   Typy ukazatelů (v kontextu unsafe). Všimněte si, že i když má ukazatel sám sebe může být volatile, objekt, který odkazuje na nelze. Jinými slovy nelze deklarovat "ukazatel na volatile."  
  
-   Typy například SByte –, bajtů, short, ushort –, int, uint, char, float a bool.  
  
-   Typ výčtu s jedním z následujících typů základní: bajtů, sbyte –, short, ushort, int nebo uint.  
  
-   Parametry obecného typu známé jako odkazové typy.  
  
-   <xref:System.IntPtr>a <xref:System.UIntPtr>.  
  
 Volatile – klíčové slovo lze použít pouze na pole třídě nebo struktuře. Místní proměnné nelze deklarovat `volatile`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat proměnnou veřejné pole jako `volatile`.  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a použít k provedení zpracování paralelně s u primární vlákno pomocné nebo pracovní vlákno. Základní informace o více vláken, viz [zřetězení](../../../standard/threading/index.md) a [zřetězení](../../programming-guide/concepts/threading/index.md).  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
