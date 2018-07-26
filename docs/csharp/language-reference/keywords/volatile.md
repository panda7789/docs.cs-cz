---
title: volatile (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 64bd5ce7d7dfe3265c3c645467493ab7d8792172
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936875"
---
# <a name="volatile-c-reference"></a>volatile (Referenční dokumentace jazyka C#)
`volatile` – Klíčové slovo určuje, že pole může být upraveno ve víc vláknech, které jsou spuštěny ve stejnou dobu. Pole, které jsou deklarovány `volatile` se nevyprázdňuje optimalizace kompilátoru, které se předpokládá přístup podle jednoho vlákna. Tato omezení Ujistěte se, že všechna vlákna budou sledovat volatile zápisy provádí ostatní vlákna v pořadí, ve kterém byly provedeny. Není zaručeno jeden celkový řazení volatile zápisů pohledu ze všech vláken, která.  
  
 `volatile` Modifikátor se obvykle používá pro pole, které je přístup prostřednictvím více vláken bez použití [Zámek](../../../csharp/language-reference/keywords/lock-statement.md) příkaz k serializaci přístup.  
  
 `volatile` – Klíčové slovo lze použít u polí těchto typů:  
  
-   Typy odkazů.  
  
-   Typy ukazatelů (v nezabezpečeném kontextu.). Všimněte si, že i když se ukazatel sám, může být typu volatile, objekt, který odkazuje na nelze. Jinými slovy nelze deklarovat "ukazatel na volatile."  
  
-   Typy, jako je například sbyte, byte, short, ushort, int, uint, char, float a bool.  
  
-   Typ výčtu s jedním z následujících základních typů: byte, sbyte, short, ushort, int nebo uint.  
  
-   Parametry obecného typu známé jako referenční typy.  
  
-   <xref:System.IntPtr> a <xref:System.UIntPtr>.  
  
 Volatile – klíčové slovo lze použít pouze pro pole třídy nebo struktury. Místní proměnné nelze použít deklaraci `volatile`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat proměnnou veřejné pole jako `volatile`.  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak můžete vytvořit a používá ke zpracování paralelní s ním primární vlákno pomocné nebo pracovní vlákno. Základní informace o multithreading, viz [dělení na spravovaná vlákna](../../../standard/threading/index.md) a [zřetězení (C#)](../../programming-guide/concepts/threading/index.md).  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
