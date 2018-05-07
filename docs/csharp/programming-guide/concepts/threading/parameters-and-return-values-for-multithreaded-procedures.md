---
title: Parametry a návratové hodnoty pro procedury ve více vláknech (C#)
ms.date: 07/20/2015
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
ms.openlocfilehash: e27f8e67ff03260e1d13fa633064efc2059e6bdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>Parametry a návratové hodnoty pro procedury ve více vláknech (C#)
Poskytnutí a vrácení hodnot v Vícevláknová aplikace je složité, protože v konstruktoru pro třídu přístup z více vláken, musí být předán odkaz na procedury, která nezadávaly žádné argumenty a nevrací žádnou hodnotu. Následující části vysvětlují, některá jednoduché způsoby, jak zadat parametry a návratové hodnoty z procedury v samostatných vláknech.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Poskytuje parametry pro procedury ve více vláknech  
 Nejlepší způsob, jak zadat parametry pro volání metody s více vlákny je zabalit do cílové metody ve třídě a definování polí pro tuto třídu, která bude sloužit jako parametry pro nové vlákno. Výhodou tohoto přístupu je, že můžete vytvořit novou instanci třídy, s vlastní parametry, pokaždé, když chcete spustit nové vlákno. Předpokládejme například, že máte funkce pro výpočet oblasti trojúhelníku, jako v následujícím kódu:  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 Můžete napsat třídu, která zabalí `CalcArea` funkce a vytvoří pole k uložení vstupních parametrů následujícím způsobem:  
  
```csharp  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 Použít `AreaClass`, můžete vytvořit `AreaClass` objektu a nastavte `Base` a `Height` vlastnosti, jak je znázorněno v následujícím kódu:  
  
```csharp  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 Všimněte si, že `TestArea` postup nekontroluje hodnotu `Area` pole po volání `CalcArea` metoda. Protože `CalcArea` běží na samostatném vlákně, `Area` pole není zaručeno, nastavit, pokud zaškrtnete ihned po volání `Thread.Start`. Další část popisuje lepší způsob vrácení hodnoty z procedury ve více vláknech.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Vrácení hodnoty z procedury ve více vláknech  
 Vrácení hodnoty z procedury, které běží v samostatných vláknech ztěžuje skutečnost, že postupy nemůže být funkce a nemůžete použít `ByRef` argumenty. Nejjednodušší způsob, jak vrátit hodnoty má používat <xref:System.ComponentModel.BackgroundWorker> součásti spravovat vaše vláken a vyvolat událost v případě, že po dokončení úkolu a zpracovat výsledky obslužnou rutinu.  
  
 Následující příklad vrací hodnotu podle vyvolání události z procedury systémem samostatné vláken:  
  
```csharp  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 Můžete zadat parametry a návratové hodnoty pro fond vláken vláken pomocí volitelného `ByVal` proměnná objekt stavu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda. Časovače vláken vláken také podporují objekt stavu pro tento účel. Informace o sdružování vláken a časovače vláken najdete v tématu [sdružování vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) a [časovače vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Multithreading s komponentou BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Přístup z více vláken sdružování (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [Synchronizace vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [Události](../../../../csharp/programming-guide/events/index.md)  
 [Vícevláknové aplikace (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegáti](../../../../csharp/programming-guide/delegates/index.md)  
 [Více vláken v součásti](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
