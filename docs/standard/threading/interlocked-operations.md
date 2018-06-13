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
ms.openlocfilehash: 38532228f7a5d07bb1b9fcf7e90d2be53a28b04c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589968"
---
# <a name="interlocked-operations"></a>Propojené operace
<xref:System.Threading.Interlocked> Třída poskytuje metody, které se synchronizují přístup k proměnné, která je sdílen více vláken. Podprocesy různé procesy můžete použít tento mechanismus, pokud je proměnná ve sdílené paměti. Propojené operace jsou atomic – celou operaci je jednotkou, která nelze přerušit jinou operací interlocked na stejnou proměnnou. To je důležité v operačních systémech s preemptivní více vláken, kde můžete vlákna pozastaví po načtení hodnotu z adresy paměti, ale před spojením šanci na změnu a uložte ho.  
  
 <xref:System.Threading.Interlocked> Třída poskytuje následující operace:  
  
-   V rozhraní .NET Framework verze 2.0 <xref:System.Threading.Interlocked.Add%2A> metoda přidá celočíselnou hodnotu do proměnné a vrátí novou hodnotu proměnné.  
  
-   V rozhraní .NET Framework verze 2.0 <xref:System.Threading.Interlocked.Read%2A> metoda čte 64bitové celé číslo hodnotu jako atomickou operaci. To je užitečné na 32bitové operační systémy, kde čtení 64bitové celé číslo není normálně atomické operace.  
  
-   <xref:System.Threading.Interlocked.Increment%2A> a <xref:System.Threading.Interlocked.Decrement%2A> metody zvýší nebo sníží proměnné a vrátí výslednou hodnotu.  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> Metoda provádí atomic výměny hodnotu do proměnné, vrátí tuto hodnotu a nahraďte ji s novou hodnotou. V rozhraní .NET Framework verze 2.0 obecný přetížení této metody slouží k provedení této exchange na proměnnou libovolného typu odkaz. V tématu <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> Metoda také výměny dvě hodnoty, ale contingent u výsledku porovnání. V rozhraní .NET Framework verze 2.0 obecný přetížení této metody slouží k provedení této exchange na proměnnou libovolného typu odkaz. V tématu <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 U moderní procesorů, metody <xref:System.Threading.Interlocked> třída může být implementována často jeden instrukcí. Proto poskytují velmi výkonné synchronizace a jde použít k sestavení vyšší úrovně synchronizace mechanismy, jako typu číselník zámky.  
  
 Pro příklad, který používá <xref:System.Threading.Monitor> a <xref:System.Threading.Interlocked> třídy v kombinaci, najdete v části [monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>Příklad CompareExchange  
 <xref:System.Threading.Interlocked.CompareExchange%2A> Metoda slouží k ochraně výpočtů, u kterých jsou složitější než jednoduché přírůstek a snížení. Následující příklad ukazuje metodu bezpečné pro přístup z více vláken, která přidá do Mezisoučet uložené jako plovoucí bodu číslo. (Pro celá čísla, <xref:System.Threading.Interlocked.Add%2A> metoda je jednodušší řešení.) Kompletní kód příklady najdete v tématu přetížení <xref:System.Threading.Interlocked.CompareExchange%2A> které přebírají jednoduchou přesností a dvojitou přesností s plovoucí desetinnou čárkou argumenty (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> a <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Netypové přetížení systému Exchange a CompareExchange  
 <xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody, mají přetížení, které nepřebírají argumenty typu <xref:System.Object>. První argument každého z těchto přetížení je `ref Object` (`ByRef … As Object` v jazyce Visual Basic), a bezpečnost typů vyžaduje proměnnou předaný tento argument výhradně zadat jako <xref:System.Object>; nejde jednoduše přetypovat na typ první argument <xref:System.Object> Při volání těchto metod.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0, použijte obecné přetížení <xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody pro výměnu silně typované proměnné.  
  
 Následující příklad kódu ukazuje vlastnost typu `ClassA` , lze nastavit pouze jednou, jak může být implementované v rozhraní .NET Framework verze 1.0 a 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
