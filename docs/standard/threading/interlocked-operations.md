---
title: Propojené operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f96286da84e41e79fb0b6253d6f20eea89da21a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201348"
---
# <a name="interlocked-operations"></a>Propojené operace

<xref:System.Threading.Interlocked?displayProperty=nameWithType> Třída poskytuje metody, které se synchronizují přístup k proměnné, které jsou sdíleny více vlákny. Vlákna různé postupy můžete použít tento mechanismus, pokud je proměnná ve sdílené paměti. Propojené operace jsou atomické – to znamená, celá operace je jednotka, která se nedá přerušit jinou operací u stejné proměnné. To je důležité v operačních systémech s preemptive multithreadingu, kde můžete vlákna pozastaví po načtení hodnoty z adresy paměti, ale před máte možnost ji změnit a uložte ho.  
  
 <xref:System.Threading.Interlocked> Třída poskytuje následující operace:  
  
-   <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> Metoda přidá celočíselnou hodnotu do proměnné a vrátí novou hodnotu proměnné.  
  
-   <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> Metoda čte 64bitové celé číslo hodnotu jako atomickou operaci. To je užitečné v 32bitové operační systémy, kde čtení 64-bit integer není obvykle atomické operace.  
  
-   <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> a <xref:System.Threading.Interlocked.Decrement%2A?displayProperty=nameWithType> metody zvýšení nebo snížení proměnné a vrátí výslednou hodnotu.  
  
-   <xref:System.Threading.Interlocked.Exchange%2A?displayProperty=nameWithType> Metoda provádí atomické výměny hodnotu do proměnné, vrátí tuto hodnotu a jeho nahrazení atributem novou hodnotu. Použití obecného <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29> přetížení této metody k provedení exchange u proměnné jakéhokoliv odkazového typu.  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A?displayProperty=nameWithType> Metoda také vymění dvě hodnoty, ale závislé na výsledku porovnání. Použití obecného <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> přetížení této metody k provedení exchange u proměnné jakéhokoliv odkazového typu.  
  
 Na moderních procesory, metody <xref:System.Threading.Interlocked> třídy může být implementována často jediná instrukce. Proto poskytují velmi výkonné synchronizace a je možné vytvářet vyšší úrovně mechanismy synchronizace, otočný zámky, jako je.  
  
 Příklad, který se používá <xref:System.Threading.Monitor> a <xref:System.Threading.Interlocked> naleznete v tématu třídy v kombinaci, <xref:System.Threading.Monitor>.  
  
## <a name="compareexchange-example"></a>Příklad CompareExchange

 <xref:System.Threading.Interlocked.CompareExchange%2A> Metodu lze použít k ochraně výpočty, které jsou složitější než jednoduché Inkrementace a dekrementace. Následující příklad ukazuje metodu bezpečným pro vlákno, které přidají průběžný celkový součet uložené jako plovoucí číslo bodu. (Pro celá čísla, <xref:System.Threading.Interlocked.Add%2A> metoda je jednodušší řešení.) Kompletní kód příkladů, naleznete v tématu přetížení <xref:System.Threading.Interlocked.CompareExchange%2A> , která přijímá argumenty jednoduchou přesností a dvojité přesnosti s plovoucí desetinnou čárkou (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> a <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Netypové přetížení systému Exchange a CompareExchange

 <xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody mají přetížení, která přijímají argumenty typu <xref:System.Object>. Prvním argumentem funkce všech tato přetížení je `ref Object` (`ByRef … As Object` v jazyce Visual Basic), a bezpečnost typů vyžaduje proměnnou předat tento argument být typu striktně <xref:System.Object>; nelze jednoduše převést na typ prvního argumentu <xref:System.Object> Při volání těchto metod.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0 nebo novější, použijte obecné přetížení <xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody k výměně silně typované proměnné.  
  
 Následující příklad kódu ukazuje vlastnost typu `ClassA` , které lze nastavit pouze jednou, protože může být implementováno v rozhraní .NET Framework verze 1.0 nebo 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Interlocked?displayProperty=nameWithType>  
- <xref:System.Threading.Monitor?displayProperty=nameWithType>  
- [Dělení na vlákna](index.md)  
- [Práce s vlákny funkce a objekty](threading-objects-and-features.md)
