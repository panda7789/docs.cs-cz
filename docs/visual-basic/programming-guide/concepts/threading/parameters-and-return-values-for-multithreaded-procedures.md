---
title: Parametry a návratové hodnoty pro procedury ve více vláknech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 545da3e89d44c29c67784b5f01812d87350030c6
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874608"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Parametry a návratové hodnoty pro procedury ve více vláknech (Visual Basic)
Zadávání a vrací hodnoty ve vícevláknových aplikacích je složitější, protože konstruktor třídy vlákno musí být předán odkaz na proceduru, která nepřijímá žádné argumenty a nevrací žádnou hodnotu. V následujících částech se dozvíte některé jednoduché způsoby, jak zadat parametry a návratové hodnoty z procedury v samostatných vláknech.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Poskytuje parametry pro procedury ve více vláknech  
 Nejlepší způsob, jak zadat parametry pro volání metody s více vlákny je zabalit cílové metody ve třídě a definování polí pro danou třídu, která bude sloužit jako parametry pro nové vlákno. Výhodou tohoto přístupu je, že pokaždé, když chcete vytvořit nové vlákno, můžete vytvořit novou instanci třídy, s vlastní parametry. Předpokládejme například, že máte funkci, která vypočítá trojúhelník, stejně jako v následujícím kódu:  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Můžete napsat třídu, která zabalí `CalcArea` funkce a vytvoří pole k uložení vstupních parametrů, následujícím způsobem:  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 Použít `AreaClass`, můžete vytvořit `AreaClass` objektu a nastavit `Base` a `Height` vlastnosti, jak je znázorněno v následujícím kódu:  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 Všimněte si, že `TestArea` postup neprovede kontrolu hodnoty `Area` pole po volání `CalcArea` metody. Protože `CalcArea` běží v samostatném vlákně, `Area` není zaručeno, že pole lze nastavit, pokud zaškrtnete ihned po volání `Thread.Start`. Další část popisuje lepší způsob, jak vrácení hodnoty z procedury ve více vláknech.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Vrácení hodnoty z procedury ve více vláknech  
 Vrácení hodnoty z procedury, které běží v samostatných vláknech je složité tím, že postupy nemůže být funkce nelze použít `ByRef` argumenty. Nejjednodušší způsob, jak vrátit hodnoty má používat <xref:System.ComponentModel.BackgroundWorker> součásti spravovat vlákna a vyvolat událost dokončení úkolu a zpracování výsledků s obslužnou rutinu události.  
  
 Následující příklad vrátí hodnotu ve vyvolání události z běžící na samostatném vlákně procedury:  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 Můžete zadat parametry a návratové hodnoty do vláken fondu vláken pomocí volitelného `ByVal` proměnné stavu objektu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody. Vlákna vlákna časovače podporují také stav objektu pro tento účel. Informace o sdružování vláken a vlákna časovače, naleznete v tématu [sdružování vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[sdružování vláken](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) a [časovače](../../../../standard/threading/timers.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Multithreading s komponentou BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [(Visual Basic) sdružování vláken](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [Synchronizace vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Vícevláknové aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Multithreading u komponent](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
