---
title: 'Postupy: zápis metody osy LINQ to XML'
ms.date: 07/20/2015
ms.assetid: b676f025-a24c-4076-8713-aa809b2b8ce0
ms.openlocfilehash: 88a9df9a2750736cfd34b655cf3ea0f57b2bff39
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348336"
---
# <a name="how-to-write-a-linq-to-xml-axis-method-visual-basic"></a><span data-ttu-id="01685-102">Postupy: zápis metody osy LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01685-102">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>
<span data-ttu-id="01685-103">Můžete napsat vlastní metody osy pro načtení kolekcí ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="01685-103">You can write your own axis methods to retrieve collections from an XML tree.</span></span> <span data-ttu-id="01685-104">Jedním z nejlepších způsobů, jak to provést, je napsat metodu rozšíření, která vrátí kolekci prvků nebo atributů.</span><span class="sxs-lookup"><span data-stu-id="01685-104">One of the best ways to do this is to write an extension method that returns a collection of elements or attributes.</span></span> <span data-ttu-id="01685-105">Můžete napsat metodu rozšíření, která vrátí konkrétní podmnožinu prvků nebo atributů na základě požadavků vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="01685-105">You can write your extension method to return specific subsets of elements or attributes, based on the requirements of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01685-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="01685-106">Example</span></span>  
 <span data-ttu-id="01685-107">Následující příklad používá dvě metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="01685-107">The following example uses two extension methods.</span></span> <span data-ttu-id="01685-108">První rozšiřující metoda, `GetXPath`pracuje na <xref:System.Xml.Linq.XObject>a vrátí výraz XPath, který při vyhodnocování vrátí uzel nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="01685-108">The first extension method, `GetXPath`, operates on <xref:System.Xml.Linq.XObject>, and returns an XPath expression that when evaluated will return the node or attribute.</span></span> <span data-ttu-id="01685-109">Druhá rozšiřující metoda, `Find`pracuje na <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="01685-109">The second extension method, `Find`, operates on <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="01685-110">Vrátí kolekci objektů <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement> objektů, které obsahují nějaký zadaný text.</span><span class="sxs-lookup"><span data-stu-id="01685-110">It returns a collection of <xref:System.Xml.Linq.XAttribute> objects and <xref:System.Xml.Linq.XElement> objects that contain some specified text.</span></span>  
  
 <span data-ttu-id="01685-111">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="01685-111">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports System.Text  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders = XElement.Load("..\..\PurchaseOrders.xml")  
  
        Dim subset = From xobj In purchaseOrders.Find("1999")  
  
        For Each obj In subset  
            Console.WriteLine(obj.GetXPath())  
            If obj.GetType() = GetType(XElement) Then  
                Console.WriteLine(CType(obj, XElement).Value)  
            ElseIf obj.GetType() = GetType(XAttribute) Then  
                Console.WriteLine(CType(obj, XAttribute).Value)  
            End If  
        Next  
    End Sub  
End Module  
  
Public Module MyExtensions  
  
    Private Function GetQName(ByVal xe As XElement) As String  
        Dim prefix = xe.GetPrefixOfNamespace(xe.Name.Namespace)  
        If xe.Name.Namespace = XNamespace.None OrElse prefix Is Nothing Then  
            Return xe.Name.LocalName  
        Else  
            Return prefix & ":" & xe.Name.LocalName  
        End If  
    End Function  
  
    Private Function GetQName(ByVal xa As XAttribute) As String  
        Dim prefix = xa.Parent.GetPrefixOfNamespace(xa.Name.Namespace)  
        If xa.Name.Namespace = XNamespace.None OrElse prefix Is Nothing Then  
            Return xa.Name.LocalName  
        Else  
            Return prefix & ":" & xa.Name.LocalName  
        End If  
    End Function  
  
    Private Function NameWithPredicate(ByVal el As XElement) As String  
        If el.Parent IsNot Nothing AndAlso  
           el.Parent.Elements(el.Name).Count() <> 1 Then  
            Return GetQName(el) & "[" &  
                (el.ElementsBeforeSelf(el.Name).Count() + 1) & "]"  
        Else  
            Return GetQName(el)  
        End If  
    End Function  
  
    <Extension()>  
    Public Function StrCat(Of T)(ByVal source As IEnumerable(Of T),  
                                 ByVal separator As String) As String  
        Return source.Aggregate(New StringBuilder,  
                                Function(sb, i) sb.  
                                    Append(i.ToString()).  
                                    Append(separator),  
                                    Function(s) s.ToString())  
    End Function  
  
    <Extension()>  
    Public Function GetXPath(ByVal xobj As XObject) As String  
  
        If xobj.Parent Is Nothing Then  
            Dim doc = TryCast(xobj, XDocument)  
            If doc IsNot Nothing Then Return "."  
  
            Dim el = TryCast(xobj, XElement)  
            If el IsNot Nothing Then Return "/" + NameWithPredicate(el)  
  
            ' the XPath data model does not include white space text nodes  
            ' that are children of a document, so this method returns null.  
  
            Dim xt = TryCast(xobj, XText)  
            If xt IsNot Nothing Then Return Nothing  
  
            Dim com = TryCast(xobj, XComment)  
            If com IsNot Nothing Then  
                Return "/" &  
                    If(com.Document.Nodes().OfType(Of XComment)().Count() <> 1,  
                       "comment()[" & (com.NodesBeforeSelf().OfType(Of XComment)().Count() + 1) & "]",  
                       "comment()")  
            End If  
  
            Dim pi = TryCast(xobj, XProcessingInstruction)  
            If pi IsNot Nothing Then  
                Return "/" &  
                    If(pi.Document.Nodes().OfType(Of XProcessingInstruction)().Count() <> 1,  
                       "processing-instruction()[" &  
                           (pi.NodesBeforeSelf().OfType(Of XProcessingInstruction)().Count() + 1) & "]",  
                       "processing-instruction()")  
            End If  
            Return Nothing  
        Else  
            Dim el = TryCast(xobj, XElement)  
            If el IsNot Nothing Then  
                Return "/" &  
                    el.Ancestors().  
                    InDocumentOrder().  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") & NameWithPredicate(el)  
            End If  
            Dim at = TryCast(xobj, XAttribute)  
            If at IsNot Nothing Then  
                Return "/" &  
                    at.Parent.  
                    AncestorsAndSelf().  
                    InDocumentOrder().  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") & "@" & GetQName(at)  
            End If  
            Dim com = TryCast(xobj, XComment)  
            If com IsNot Nothing Then  
                Return "/" &  
                    com.Parent.  
                    AncestorsAndSelf().  
                    InDocumentOrder().  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") &  
                        If(com.Parent.Nodes().OfType(Of XComment)().Count() <> 1,  
                           "comment()[" & (com.NodesBeforeSelf().OfType(Of XComment)().Count() + 1) & "]",  
                           "comment()")  
            End If  
  
            Dim cd = TryCast(xobj, XCData)  
            If cd IsNot Nothing Then  
                Return "/" &  
                    cd.Parent.  
                    AncestorsAndSelf().  
                    InDocumentOrder().  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") &  
                        If(cd.Parent.Nodes().OfType(Of XText)().Count() <> 1,  
                           "text()[" & (cd.NodesBeforeSelf().OfType(Of XText)().Count() + 1) & "]",  
                           "text()")  
            End If  
            Dim tx = TryCast(xobj, XText)  
            If tx IsNot Nothing Then  
                Return "/" &  
                    tx.Parent.  
                    AncestorsAndSelf().  
                    InDocumentOrder().  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") &  
                        If(tx.Parent.Nodes().OfType(Of XText)().Count() <> 1,  
                           "text()[" & (tx.NodesBeforeSelf().OfType(Of XText)().Count() + 1) & "]",  
                           "text()")  
            End If  
            Dim pi As XProcessingInstruction = TryCast(xobj, XProcessingInstruction)  
            If pi IsNot Nothing Then  
                Return "/" &  
                    pi.Parent.  
                    AncestorsAndSelf().  
                    InDocumentOrder().  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") &  
                        If(pi.Parent.Nodes().OfType(Of XProcessingInstruction)().Count() <> 1,  
                           "processing-instruction()[" &  
                               (pi.NodesBeforeSelf().OfType(Of XProcessingInstruction)().Count() + 1) & "]",  
                           "processing-instruction()")  
            End If  
            Return Nothing  
        End If  
    End Function  
  
    <Extension()>  
    Public Function Find(ByVal source As XElement, ByVal value As String) As IEnumerable(Of XObject)  
        Dim results = From att In source.Attributes()  
                      Where att.Value.Contains(value)  
                      Let a As XObject = att  
                      Select a  
  
        If source.Elements().Any Then  
            For Each result In From child In source.Elements() Select Find(child, value)  
                results = If(results Is Nothing, result, results.Union(result))  
            Next  
        Else  
            If source.Value.Contains(value) Then  
                results = If(results Is Nothing,  
                             New List(Of XObject) From {source},  
                             results.Union(New List(Of XObject) From {source}))  
            End If  
        End If  
  
        Return results  
    End Function  
  
End Module  
```  
  
 <span data-ttu-id="01685-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="01685-112">This code produces the following output:</span></span>  
  
```console  
/PurchaseOrders/PurchaseOrder[1]/@OrderDate  
1999-10-20  
/PurchaseOrders/PurchaseOrder[1]/Items/Item[2]/ShipDate  
1999-05-21  
/PurchaseOrders/PurchaseOrder[2]/@OrderDate  
1999-10-22  
/PurchaseOrders/PurchaseOrder[3]/@OrderDate  
1999-10-22  
```  
  
## <a name="see-also"></a><span data-ttu-id="01685-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01685-113">See also</span></span>

- [<span data-ttu-id="01685-114">Pokročilé techniky dotazů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01685-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
