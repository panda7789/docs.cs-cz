---
title: 'Postupy: Stream fragmenty XML z objekt XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 38a81e83421dffc997a2cbfd6d0996da5ece18d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643354"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Postupy: Stream fragmenty XML z objekt XmlReader (Visual Basic)
Až budete mít ke zpracování velkých souborů XML, nemusí být vhodný načíst celý strom XML do paměti. Toto téma ukazuje, jak k vysílání datového proudu fragmenty pomocí <xref:System.Xml.XmlReader>.  
  
 Jedním z nejúčinnějších způsobů, jak používat <xref:System.Xml.XmlReader> číst <xref:System.Xml.Linq.XElement> objektů je napsat vlastní metodu vlastní osy. Metodu osy, jako obvykle vrátí kolekci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu. V metodě vlastní osy, po vytvoření XML fragment voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metoda, vrátí kolekce používá `yield return`. To poskytuje sémantiku odložené provedení metodu vlastní osy.  
  
 Když vytvoříte strom XML z <xref:System.Xml.XmlReader> objekt, <xref:System.Xml.XmlReader> musí být umístěn v elementu. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nevrátí před přečtením značka ukončení elementu.  
  
 Pokud chcete vytvořit částečné stromové struktury, můžete vytvořit instanci <xref:System.Xml.XmlReader>, pozice čtenáře na uzlu, který chcete převést na <xref:System.Xml.Linq.XElement> stromu a pak vytvořte <xref:System.Xml.Linq.XElement> objektu.  
  
 Téma [postup: datový proud XML fragmenty se přístup k informacím o záhlaví (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad o tom, jak stream složitější dokumentu.  
  
 Téma [postup: provedení vysílání datového proudu transformace z velké dokumentů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití technologie LINQ to XML k transformaci velmi velký dokumentů XML při zachování nároků paměti.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří vlastní osy metoda. Se můžete dotazovat pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu. Metodu vlastní osy `StreamRootChildDoc`, je metoda, která je určená speciálně pro čtení dokumentu, který má opakující se `Child` elementu.  
  
```vb  
Module Module1  
    Sub Main()  
        Dim markup = "<Root>" &  
                     "  <Child Key=""01"">" &  
                     "    <GrandChild>aaa</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""02"">" &  
                     "    <GrandChild>bbb</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""03"">" &  
                     "    <GrandChild>ccc</GrandChild>" &  
                     "  </Child>" &  
                     "</Root>"  
  
        Dim grandChildData =  
             From el In New StreamRootChildDoc(New IO.StringReader(markup))  
             Where CInt(el.@Key) > 1  
             Select el.<GrandChild>.Value  
  
        For Each s In grandChildData  
            Console.WriteLine(s)  
        Next  
    End Sub  
End Module  
  
Public Class StreamRootChildDoc  
    Implements IEnumerable(Of XElement)  
  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamChildEnumerator(_stringReader)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamChildEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _reader As Xml.XmlReader  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        While _reader.Read()  
            Select Case _reader.NodeType  
                Case Xml.XmlNodeType.Element  
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)  
                    If el IsNot Nothing Then  
                        _current = el  
                        Return True  
                    End If  
            End Select  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
bbb  
ccc  
```  
  
 V tomto příkladu jsou velmi malé zdrojový dokument. Ale i v případě, že bylo miliony `Child` elementy, v tomto příkladu by mít stále malou paměťovou zátěž.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Implementace IEnumerable(Of T) v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
