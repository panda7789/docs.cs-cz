---
title: Přístup z více vláken sdružování (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
ms.openlocfilehash: 445c1c70cc1371ef918f32046e0c30ae2a473da2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="thread-pooling-visual-basic"></a>Přístup z více vláken sdružování (Visual Basic)
A *fondu vláken* je kolekce vláken, které lze použít k provedení některých úloh na pozadí. (Viz [zřetězení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) základní informace.) Zůstane primární bezplatné provést další úlohy asynchronně vlákno.  
  
 Fondy vláken jsou často používané v serverových aplikací. Každého příchozího požadavku je přiřazen k vlákno z fondu podprocesů tak, aby požadavek může zpracovat asynchronně, bez třeba zadávat primární vlákno nebo zpozdit zpracování následných žádostí.  
  
 Po dokončení úkolu vláken ve fondu se vrátí do fronty čekání vláken, kde ji můžete znovu použít. Tato opakované použití umožňuje aplikacím vyhnout náklady na vytvoření nové vlákno pro každou úlohu.  
  
 Fondy vláken obvykle mají maximální počet vláken. Pokud jsou všechna vlákna zaneprázdněný, další úkoly jsou umístěna do fronty, dokud se zpracováním vláken dostupná.  
  
 Můžete implementovat vlastní fond vláken, ale je jednodušší použít poskytované rozhraní .NET Framework prostřednictvím fondu vláken <xref:System.Threading.ThreadPool> třídy.  
  
 S sdružování vláken zavoláte <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> metoda s delegáta pro postup, který chcete spustit, a Visual Basic vytvoří vlákno a spouští procedury.  
  
## <a name="thread-pooling-example"></a>Příklad sdružování vláken  
 Následující příklad ukazuje, jak je možné používat vlákno sdružování spustit několik úloh.  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 Jednou z výhod sdružování vláken je, že můžete předat argumenty v objektu stavu k postupu úloh. Pokud jsou volání procedura vyžaduje více než jeden argument, může odevzdat strukturou nebo instance třídy do `Object` datového typu.  
  
## <a name="thread-pool-parameters-and-return-values"></a>Vlákno fondu parametry a návratové hodnoty  
 Vrácení hodnoty z vlákna, fondu vláken není jasné. Standardní způsob vrácení hodnot z volání funkce není povolena, protože `Sub` postupy jsou jediným typem procedury, která může zařazených do fronty pro fond vláken. Jedním ze způsobů, můžete zadat parametry a vrátí hodnoty, je zabalení parametry, vrácených hodnot, a metody v obálce třídy, jak je popsáno v [parametry a vrátí hodnoty pro procedury ve více vláknech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 O easer způsob, jak zadat parametry a návratové hodnoty je pomocí volitelného `ByVal` proměnné objektu stavu systému <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda. Pokud použijete tuto proměnnou k předání odkaz na instanci třídy, můžete členů instance upraveném vlákno fondu vláken a použít jako návratové hodnoty.  
  
 Zpočátku nemusí být zřejmé, že můžete upravit objekt, na kterou odkazuje proměnná, která je předaná hodnota. To můžete provést, protože pouze odkaz na objekt je předaná hodnota. Pokud provedete změny členům objektu, na kterou odkazuje odkaz na objekt, použít změny instance třídy skutečný.  
  
 Struktury nelze použít k návratu hodnot uvnitř stavu objektů. Protože struktury jsou typy hodnot, neměňte změny, které provede asynchronní proces členů původní struktura. Návratové hodnoty nejsou potřebné zajistit parametry používejte struktury.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Postupy: použití fondu vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [Dělení na vlákna (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [Vícevláknové aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Synchronizace vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
