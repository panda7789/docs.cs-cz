---
title: Přístup z více vláken sdružování (C#)
ms.date: 07/20/2015
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
ms.openlocfilehash: 42e1dcedc1897dc82bbd13f12882cbef6a5da4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="thread-pooling-c"></a>Přístup z více vláken sdružování (C#)
A *fondu vláken* je kolekce vláken, které lze použít k provedení některých úloh na pozadí. (Viz [zřetězení (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) základní informace.) Zůstane primární bezplatné provést další úlohy asynchronně vlákno.  
  
 Fondy vláken jsou často používané v serverových aplikací. Každého příchozího požadavku je přiřazen k vlákno z fondu podprocesů tak, aby požadavek může zpracovat asynchronně, bez třeba zadávat primární vlákno nebo zpozdit zpracování následných žádostí.  
  
 Po dokončení úkolu vláken ve fondu se vrátí do fronty čekání vláken, kde ji můžete znovu použít. Tato opakované použití umožňuje aplikacím vyhnout náklady na vytvoření nové vlákno pro každou úlohu.  
  
 Fondy vláken obvykle mají maximální počet vláken. Pokud jsou všechna vlákna zaneprázdněný, další úkoly jsou umístěna do fronty, dokud se zpracováním vláken dostupná.  
  
 Můžete implementovat vlastní fond vláken, ale je jednodušší použít poskytované rozhraní .NET Framework prostřednictvím fondu vláken <xref:System.Threading.ThreadPool> třídy.  
  
 S sdružování vláken zavoláte <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> metoda s delegáta pro postup, který chcete spustit, a C# vytvoří vlákno a spustí procedury.  
  
## <a name="thread-pooling-example"></a>Příklad sdružování vláken  
 Následující příklad ukazuje, jak je možné používat vlákno sdružování spustit několik úloh.  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 Jednou z výhod sdružování vláken je, že můžete předat argumenty v objektu stavu k postupu úloh. Pokud jsou volání procedura vyžaduje více než jeden argument, může odevzdat strukturou nebo instance třídy do `Object` datového typu.  
  
## <a name="thread-pool-parameters-and-return-values"></a>Vlákno fondu parametry a návratové hodnoty  
 Vrácení hodnoty z vlákna, fondu vláken není jasné. Standardní způsob vrácení hodnot z volání funkce není povolena, protože `Sub` postupy jsou jediným typem procedury, která může zařazených do fronty pro fond vláken. Jedním ze způsobů, můžete zadat parametry a vrátí hodnoty, je zabalení parametry, vrácených hodnot, a metody v obálce třídy, jak je popsáno v [parametry a vrátí hodnoty pro procedury ve více vláknech (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 Snadný způsob, jak zadat parametry a návratové hodnoty je pomocí volitelného `ByVal` proměnné objektu stavu systému <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda. Pokud použijete tuto proměnnou k předání odkaz na instanci třídy, můžete členů instance upraveném vlákno fondu vláken a použít jako návratové hodnoty.  
  
 Zpočátku nemusí být zřejmé, že můžete upravit objekt, na kterou odkazuje proměnná, která je předaná hodnota. To můžete provést, protože pouze odkaz na objekt je předaná hodnota. Pokud provedete změny členům objektu, na kterou odkazuje odkaz na objekt, použít změny instance třídy skutečný.  
  
 Struktury nelze použít k návratu hodnot uvnitř stavu objektů. Protože struktury jsou typy hodnot, neměňte změny, které provede asynchronní proces členů původní struktura. Návratové hodnoty nejsou potřebné zajistit parametry používejte struktury.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Postupy: použití fondu vláken (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [Dělení na vlákna (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Vícevláknové aplikace (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Synchronizace vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
