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
ms.openlocfilehash: 6478ea94b6c54272a01497ac7b1cb1b197892309
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527483"
---
# <a name="interlocked-operations"></a>Propojené operace
<xref:System.Threading.Interlocked> Třída poskytuje metody, které se synchronizují přístup k proměnné, které jsou sdíleny více vlákny. Vlákna různé postupy můžete použít tento mechanismus, pokud je proměnná ve sdílené paměti. Propojené operace jsou atomické – to znamená, celá operace je jednotka, která se nedá přerušit jinou operací propojené na stejnou proměnnou. To je důležité v operačních systémech s preemptive multithreadingu, kde můžete vlákna pozastaví po načtení hodnoty z adresy paměti, ale před máte možnost ji změnit a uložte ho.  
  
 <xref:System.Threading.Interlocked> Třída poskytuje následující operace:  
  
-   V rozhraní .NET Framework verze 2.0 <xref:System.Threading.Interlocked.Add%2A> metoda přidá celočíselnou hodnotu do proměnné a vrátí novou hodnotu proměnné.  
  
-   V rozhraní .NET Framework verze 2.0 <xref:System.Threading.Interlocked.Read%2A> metoda čte 64bitové celé číslo hodnotu jako atomickou operaci. To je užitečné v 32bitové operační systémy, kde čtení 64-bit integer není obvykle atomické operace.  
  
-   <xref:System.Threading.Interlocked.Increment%2A> a <xref:System.Threading.Interlocked.Decrement%2A> metody zvýšení nebo snížení proměnné a vrátí výslednou hodnotu.  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> Metoda provádí atomické výměny hodnotu do proměnné, vrátí tuto hodnotu a jeho nahrazení atributem novou hodnotu. V rozhraní .NET Framework verze 2.0 je možné obecné přetížení této metody k provedení této exchange u proměnné jakéhokoliv odkazového typu. Zobrazit <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> Metoda také vymění dvě hodnoty, ale závislé na výsledku porovnání. V rozhraní .NET Framework verze 2.0 je možné obecné přetížení této metody k provedení této exchange u proměnné jakéhokoliv odkazového typu. Zobrazit <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 Na moderních procesory, metody <xref:System.Threading.Interlocked> třídy může být implementována často jediná instrukce. Proto poskytují velmi výkonné synchronizace a je možné vytvářet vyšší úrovně mechanismy synchronizace, otočný zámky, jako je.  
  
 Příklad, který se používá <xref:System.Threading.Monitor> a <xref:System.Threading.Interlocked> naleznete v tématu třídy v kombinaci, [monitorování](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>Příklad CompareExchange  
 <xref:System.Threading.Interlocked.CompareExchange%2A> Metodu lze použít k ochraně výpočty, které jsou složitější než jednoduché Inkrementace a dekrementace. Následující příklad ukazuje metodu bezpečným pro vlákno, které přidají průběžný celkový součet uložené jako plovoucí číslo bodu. (Pro celá čísla, <xref:System.Threading.Interlocked.Add%2A> metoda je jednodušší řešení.) Kompletní kód příkladů, naleznete v tématu přetížení <xref:System.Threading.Interlocked.CompareExchange%2A> , která přijímá argumenty jednoduchou přesností a dvojité přesnosti s plovoucí desetinnou čárkou (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> a <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Netypové přetížení systému Exchange a CompareExchange  
 <xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody mají přetížení, která přijímají argumenty typu <xref:System.Object>. Prvním argumentem funkce všech tato přetížení je `ref Object` (`ByRef … As Object` v jazyce Visual Basic), a bezpečnost typů vyžaduje proměnnou předat tento argument být typu striktně <xref:System.Object>; nelze jednoduše převést na typ prvního argumentu <xref:System.Object> Při volání těchto metod.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0, použijte obecné přetížení <xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody k výměně silně typované proměnné.  
  
 Následující příklad kódu ukazuje vlastnost typu `ClassA` , které lze nastavit pouze jednou, protože může být implementováno v rozhraní .NET Framework verze 1.0 nebo 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Interlocked>  
- <xref:System.Threading.Monitor>  
- [Dělení na vlákna](../../../docs/standard/threading/index.md)  
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
