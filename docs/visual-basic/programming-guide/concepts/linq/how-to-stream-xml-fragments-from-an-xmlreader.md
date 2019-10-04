---
title: 'Postupy: streamování fragmentů XML ze třídy XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 3edb9cbbe9b649a5b4d232a3937e6f322b4a6b7d
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835149"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Postupy: streamování fragmentů XML ze třídy XmlReader (Visual Basic)
V případě potřeby zpracování velkých souborů XML nemusí být možné načíst celý strom XML do paměti. Toto téma ukazuje, jak streamovat fragmenty pomocí <xref:System.Xml.XmlReader>.  
  
 Jedním z nejúčinnějších způsobů, jak použít <xref:System.Xml.XmlReader> ke čtení objektů <xref:System.Xml.Linq.XElement>, je napsat vlastní metodu vlastní osy. Metoda Axis obvykle vrací kolekci, jako je například <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu. V metodě vlastní osy po vytvoření fragmentu XML voláním metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> vraťte kolekci pomocí `yield return`. To poskytuje sémantiku pro odložené provádění vlastní metody osy.  
  
 Při vytváření stromu XML z objektu @no__t 0 musí být <xref:System.Xml.XmlReader> umístěn na elementu. Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> se nevrátí, dokud nepřečetla uzavírací značku elementu.  
  
 Pokud chcete vytvořit částečný strom, můžete vytvořit instanci <xref:System.Xml.XmlReader>, umístit čtecí modul na uzel, který chcete převést na strom <xref:System.Xml.Linq.XElement>, a pak vytvořit objekt <xref:System.Xml.Linq.XElement>.  
  
 Téma [Postupy: streamování fragmentů XML s přístupem k informacím hlavičky (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad, jak streamovat složitější dokument.  
  
 Téma [Postupy: provedení transformace streamování velkých dokumentů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití LINQ to XML k transformaci extrémně velkých dokumentů XML při zachování malých nároků na paměť.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří vlastní metodu osy. Můžete na ně zadat dotaz pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Vlastní metoda osy `StreamRootChildDoc` je metoda, která je navržena speciálně pro čtení dokumentu, který má opakující se prvek `Child`.  
  
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
  
```console  
bbb  
ccc  
```  
  
 V tomto příkladu je zdrojový dokument velmi malý. Nicméně i v případě, že existovaly miliony prvků `Child`, bude mít tento příklad pořád malou paměť.  
  
## <a name="see-also"></a>Viz také:

- [Návod: implementace IEnumerable (Of T) v Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
