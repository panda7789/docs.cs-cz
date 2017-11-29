---
title: "Postupy: Přístup ke třídě kolekce pomocí příkazu foreach (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cf827e958d4dc3b951d17b53effd155356c0ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a>Postupy: Přístup ke třídě kolekce pomocí příkazu foreach (Průvodce programováním v C#)
Následující příklad kódu ukazuje, jak napsat negenerická kolekce třídu, která lze použít s [foreach](../../../csharp/language-reference/keywords/foreach-in.md). Tento příklad definuje třídu tokenizátor řetězec.  
  
> [!NOTE]
>  V tomto příkladu představuje doporučený postup jenom v případě, že nelze použít třídu obecné kolekce. Příklad toho, jak implementovat třídu obecné typově bezpečné kolekce, která podporuje <xref:System.Collections.Generic.IEnumerable%601>, najdete v části [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
 V příkladu následující kód používá segmentu `Tokens` třídy pro přerušení větu "Toto je ukázkový věty." do tokenů pomocí ' ' a '-' jako oddělovače. Kód pak zobrazí tyto tokeny pomocí `foreach` příkaz.  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a>Příklad  
 Interně `Tokens` třída používá pole k uložení tokenů. Vzhledem k tomu pole implementujete <xref:System.Collections.IEnumerator> a <xref:System.Collections.IEnumerable>, příklad kódu může použili metody pole – výčet (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, a <xref:System.Collections.IEnumerator.Current%2A>) místo nich definování `Tokens` – třída. Metoda definice jsou zahrnuty v příkladu o vysvětlení, jak jsou definovány a co každý nemá.  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 V jazyce C#, není nutné pro třídu kolekce k implementaci <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> být kompatibilní s `foreach`. Pokud třída nemá požadované <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, a <xref:System.Collections.IEnumerator.Current%2A> členy, bude fungovat s `foreach`. Vynechání rozhraní nabízí výhodu v podobě umožňuje definovat návratový typ pro `Current` který je specifičtější než <xref:System.Object>. To poskytuje bezpečnost typů.  
  
 Můžete například změňte následující řádky v předchozím příkladu.  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 Protože `Current` vrátí řetězec, kompilátor může rozpoznat, kdy se nekompatibilní typ se používá v `foreach` příkaz, jak je znázorněno v následujícím kódu.  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 Nevýhodou vynechání <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> je, že třída kolekce je už vzájemná spolupráce s `foreach` příkazy nebo ekvivalentní příkazy další běžné jazyků runtime jazyka.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Kolekce](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
