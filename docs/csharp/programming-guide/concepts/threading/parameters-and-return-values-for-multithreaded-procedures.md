---
title: Parametry a návratové hodnoty pro procedury ve více vláknech (C#)
ms.date: 07/20/2015
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
ms.openlocfilehash: 218e297d192d37d55ff391045342262d7bf66a0c
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875121"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>Parametry a návratové hodnoty pro procedury ve více vláknech (C#)
Zadávání a vrací hodnoty ve vícevláknových aplikacích je složitější, protože konstruktor třídy vlákno musí být předán odkaz na proceduru, která nepřijímá žádné argumenty a nevrací žádnou hodnotu. V následujících částech se dozvíte některé jednoduché způsoby, jak zadat parametry a návratové hodnoty z procedury v samostatných vláknech.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Poskytuje parametry pro procedury ve více vláknech  
 Nejlepší způsob, jak zadat parametry pro volání metody s více vlákny je zabalit cílové metody ve třídě a definování polí pro danou třídu, která bude sloužit jako parametry pro nové vlákno. Výhodou tohoto přístupu je, že pokaždé, když chcete vytvořit nové vlákno, můžete vytvořit novou instanci třídy, s vlastní parametry. Předpokládejme například, že máte funkci, která vypočítá trojúhelník, stejně jako v následujícím kódu:  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 Můžete napsat třídu, která zabalí `CalcArea` funkce a vytvoří pole k uložení vstupních parametrů, následujícím způsobem:  
  
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
  
 Použít `AreaClass`, můžete vytvořit `AreaClass` objektu a nastavit `Base` a `Height` vlastnosti, jak je znázorněno v následujícím kódu:  
  
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
  
 Všimněte si, že `TestArea` postup neprovede kontrolu hodnoty `Area` pole po volání `CalcArea` metody. Protože `CalcArea` běží v samostatném vlákně, `Area` není zaručeno, že pole lze nastavit, pokud zaškrtnete ihned po volání `Thread.Start`. Další část popisuje lepší způsob, jak vrácení hodnoty z procedury ve více vláknech.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Vrácení hodnoty z procedury ve více vláknech  
 Vrácení hodnoty z procedury, které běží v samostatných vláknech je složité tím, že postupy nemůže být funkce nelze použít `ByRef` argumenty. Nejjednodušší způsob, jak vrátit hodnoty má používat <xref:System.ComponentModel.BackgroundWorker> součásti spravovat vlákna a vyvolat událost dokončení úkolu a zpracování výsledků s obslužnou rutinu události.  
  
 Následující příklad vrátí hodnotu ve vyvolání události z běžící na samostatném vlákně procedury:  
  
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
  
 Můžete zadat parametry a návratové hodnoty do vláken fondu vláken pomocí volitelného `ByVal` proměnné stavu objektu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody. Vlákna vlákna časovače podporují také stav objektu pro tento účel. Informace o sdružování vláken a vlákna časovače, naleznete v tématu [sdružování vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) a [časovače](../../../../standard/threading/timers.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Multithreading s komponentou BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Vlákno sdružování (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [Synchronizace vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [Události](../../../../csharp/programming-guide/events/index.md)  
 [Vícevláknové aplikace (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegáti](../../../../csharp/programming-guide/delegates/index.md)  
 [Multithreading u komponent](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
