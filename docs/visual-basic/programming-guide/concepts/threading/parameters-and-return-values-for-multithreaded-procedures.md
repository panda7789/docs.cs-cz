---
title: Parametry a návratové hodnoty pro procedury ve více vláknech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 039e9be6f174148995a83c842a442806b9409a3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648096"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Parametry a návratové hodnoty pro procedury ve více vláknech (Visual Basic)
Poskytnutí a vrácení hodnot v Vícevláknová aplikace je složité, protože v konstruktoru pro třídu přístup z více vláken, musí být předán odkaz na procedury, která nezadávaly žádné argumenty a nevrací žádnou hodnotu. Následující části vysvětlují, některá jednoduché způsoby, jak zadat parametry a návratové hodnoty z procedury v samostatných vláknech.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Poskytuje parametry pro procedury ve více vláknech  
 Nejlepší způsob, jak zadat parametry pro volání metody s více vlákny je zabalit do cílové metody ve třídě a definování polí pro tuto třídu, která bude sloužit jako parametry pro nové vlákno. Výhodou tohoto přístupu je, že můžete vytvořit novou instanci třídy, s vlastní parametry, pokaždé, když chcete spustit nové vlákno. Předpokládejme například, že máte funkce pro výpočet oblasti trojúhelníku, jako v následujícím kódu:  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Můžete napsat třídu, která zabalí `CalcArea` funkce a vytvoří pole k uložení vstupních parametrů následujícím způsobem:  
  
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
  
 Použít `AreaClass`, můžete vytvořit `AreaClass` objektu a nastavte `Base` a `Height` vlastnosti, jak je znázorněno v následujícím kódu:  
  
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
  
 Všimněte si, že `TestArea` postup nekontroluje hodnotu `Area` pole po volání `CalcArea` metoda. Protože `CalcArea` běží na samostatném vlákně, `Area` pole není zaručeno, nastavit, pokud zaškrtnete ihned po volání `Thread.Start`. Další část popisuje lepší způsob vrácení hodnoty z procedury ve více vláknech.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Vrácení hodnoty z procedury ve více vláknech  
 Vrácení hodnoty z procedury, které běží v samostatných vláknech ztěžuje skutečnost, že postupy nemůže být funkce a nemůžete použít `ByRef` argumenty. Nejjednodušší způsob, jak vrátit hodnoty má používat <xref:System.ComponentModel.BackgroundWorker> součásti spravovat vaše vláken a vyvolat událost v případě, že po dokončení úkolu a zpracovat výsledky obslužnou rutinu.  
  
 Následující příklad vrací hodnotu podle vyvolání události z procedury systémem samostatné vláken:  
  
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
  
 Můžete zadat parametry a návratové hodnoty pro fond vláken vláken pomocí volitelného `ByVal` proměnná objekt stavu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda. Časovače vláken vláken také podporují objekt stavu pro tento účel. Informace o sdružování vláken a časovače vláken najdete v tématu [sdružování vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[sdružování vláken](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) a [časovače vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Multithreading s komponentou BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Přístup z více vláken sdružování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [Synchronizace vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Vícevláknové aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Více vláken v součásti](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
