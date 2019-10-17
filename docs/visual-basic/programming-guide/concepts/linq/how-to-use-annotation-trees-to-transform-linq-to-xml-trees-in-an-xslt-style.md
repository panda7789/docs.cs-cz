---
title: 'Postupy: použití poznámek k transformaci LINQ to XMLch stromů ve stylu XSLT (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: b950f823b65299689f4ed829138a6689f6789c18
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395963"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a>Postupy: použití poznámek k transformaci LINQ to XMLch stromů ve stylu XSLT (Visual Basic)

Poznámky lze použít k usnadnění transformací stromu XML.

Některé dokumenty XML jsou "dokumenty orientované na smíšený obsah". S takovými dokumenty nemusíte nutně znát tvar podřízených uzlů prvku. Například uzel, který obsahuje text, může vypadat takto:

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

Pro libovolný daný textový uzel může existovat libovolný počet podřízených prvků `<b>` a `<i>`. Tento přístup se rozšiřuje na řadu dalších situací: například stránky, které mohou obsahovat různé podřízené prvky, jako jsou například běžné odstavce, odstavce s odrážkami a rastry. Buňky v tabulce mohou obsahovat text, rozevírací seznamy nebo rastrové obrázky. Jednou z hlavních charakteristik XML orientovaného dokumentu je, že nevíte, který podřízený prvek bude mít konkrétní prvek.

Pokud chcete transformovat prvky ve stromové struktuře, kde nevíte nutně o podřízených objektech prvků, které chcete transformovat, pak tento přístup, který používá poznámky, představuje účinný přístup.

Souhrn tohoto přístupu:

- Nejprve opatřit poznámkami prvky ve stromové struktuře náhradním elementem.

- Potom Iterujte celý strom a vytvořte nový strom, ve kterém nahradíte jednotlivé prvky jeho anotací. Tento příklad implementuje iteraci a vytvoření nového stromu ve funkci s názvem `XForm`.

Tento přístup se skládá z těchto možností:

- Proveďte jeden nebo více LINQ to XML dotazů, které vracejí sadu prvků, které chcete transformovat z jednoho obrazce na jiný. Pro každý prvek v dotazu přidejte nový objekt <xref:System.Xml.Linq.XElement> jako anotaci k elementu. Tento nový element nahradí element s poznámkou v novém, transformované stromové struktuře. Toto je jednoduchý kód pro zápis, jak je znázorněno v příkladu.

- Nový prvek, který je přidán jako anotace, může obsahovat nové podřízené uzly; může vytvořit dílčí strom s libovolným požadovaným tvarem.

- Existuje zvláštní pravidlo: Pokud je podřízený uzel nového elementu v jiném oboru názvů, který je vytvořen pro tento účel (v tomto příkladu je obor názvů `http://www.microsoft.com/LinqToXmlTransform/2007`), pak tento podřízený element není zkopírován do nového stromu. Místo toho, pokud je obor názvů výše zmíněným speciálním oborem názvů a místní název elementu je `ApplyTransforms`, pak jsou v podřízených uzlech elementu ve stromu zdrojového kódu iterace a zkopírovány do nového stromu (s výjimkou, že jsou podřízené prvky s poznámkami. Tato pravidla se transformují podle těchto pravidel.

- To je trochu podobné určení transformací v prvku XSL. Dotaz, který vybere sadu uzlů, je podobný výrazu XPath pro šablonu. Kód pro vytvoření nového <xref:System.Xml.Linq.XElement>, který je uložen jako anotace, je podobný konstruktoru sekvence v prvku XSL a prvek `ApplyTransforms` je podobný funkci jako element `xsl:apply-templates` v prvku XSL.

- Jednou z výhod tohoto přístupu – při formulování dotazů vždy zapisujete dotazy na neupravený zdrojový strom. Nemusíte si dělat starosti s tím, jak změny stromu ovlivňují dotazy, které píšete.

## <a name="transforming-a-tree"></a>Transformace stromu

Tento první příklad přejmenuje všechny uzly `Paragraph` na `para`:

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>
                <Paragraph>More text.</Paragraph>
            </Root>

        ' Replace Paragraph with p.
        For Each el In root...<Paragraph>
            ' same idea as xsl:apply-templates
            el.AddAnnotation( _
                <para>
                    <<%= at %>></>
                </para>)
        Next

        ' The XForm function, shown later in this topic, accomplishes the transform
        Dim newRoot As XElement = XForm(root)
        Console.WriteLine(newRoot)
    End Sub
End Module
```

 Tento příklad vytvoří následující výstup:

```xml
<Root>
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>
  <para>More text.</para>
</Root>
```

## <a name="a-more-complicated-transform"></a>Složitější transformace

 Následující příklad dotazuje strom a vypočítá průměr a součet prvků `Data` a přidá je jako nové prvky do stromu.

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim data As XElement = _
            <Root>
                <Data>20</Data>
                <Data>10</Data>
                <Data>3</Data>
            </Root>

        ' While adding annotations, you can query the source tree all you want,
        ' as the tree is not mutated while annotating.
        data.AddAnnotation( _
            <Root>
                <<%= at %>/>
                <Average>
                    <%= _
                        String.Format("{0:F4}", _
                        data.Elements("Data") _
                        .Select(Function(z) CDec(z)).Average()) _
                    %>
                </Average>
                <Sum>
                    <%= _
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _
                    %>
                </Sum>
            </Root> _
        )

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(data)
        Console.WriteLine(vbNewLine)

        ' The XForm function, shown later in this topic, accomplishes the transform
        Dim newData As XElement = XForm(data)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newData)
    End Sub
End Module 
```

 Tento příklad vytvoří následující výstup:

```console
Before Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
</Root>

After Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
  <Average>11.0000</Average>
  <Sum>33</Sum>
</Root>
```

## <a name="effecting-the-transform"></a>Ovlivnění transformace

Malá funkce `XForm` vytvoří nový transformovaný strom z originálu s poznámkou stromu.

Pseudo kód pro funkci je poměrně jednoduchý:

> Funkce přebírá jako argument XElement a vrátí XElement.
> 
> Pokud má element anotaci XElement, vraťte novou XElement:
>
> - Název nového XElement je název prvku poznámky.
> - Všechny atributy jsou zkopírovány z poznámky do nového uzlu.
> - Všechny podřízené uzly jsou zkopírovány z anotace s výjimkou, že speciální uzel XF: ApplyTransforms je rozpoznán a podřízené uzly zdrojového elementu jsou iterace. Pokud zdrojový podřízený uzel není XElement, je zkopírován do nového stromu. Pokud je zdrojový podřízený objekt XElement, je transformované voláním této funkce rekurzivně.
>
> Pokud element není opatřen poznámkami:
>
> - Vrátit novou XElement
>   - Název nového XElement je název zdrojového elementu.
>   - Všechny atributy jsou zkopírovány ze zdrojového elementu do elementu cíle.
>   - Všechny podřízené uzly jsou zkopírovány ze zdrojového elementu.
>   - Pokud zdrojový podřízený uzel není XElement, je zkopírován do nového stromu. Pokud je zdrojový podřízený objekt XElement, je transformované voláním této funkce rekurzivně.

Následující kód je implementace této funkce:

```vb
' Build a transformed XML tree per the annotations.
Function XForm(ByVal source As XElement) As XElement
    If source.Annotation(Of XElement)() IsNot Nothing Then
        Dim anno As XElement = source.Annotation(Of XElement)()
        Return _
            <<%= anno.Name.ToString() %>>
                <%= anno.Attributes() %>
                <%= anno.Nodes().Select(Function(n As XNode) _
                    GetSubNodes(n, source)) %>
            </>
    Else
        Return _
            <<%= source.Name %>>
                <%= source.Attributes() %>
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
            </>
    End If
End Function

Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
    Dim annoEl As XElement = TryCast(n, XElement)
    If annoEl IsNot Nothing Then
        If annoEl.Name = at Then
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
        End If
    End If
    Return n
End Function

Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
    Dim e2 As XElement = TryCast(n2, XElement)
    If e2 Is Nothing Then
        Return n2
    Else
        Return XForm(e2)
    End If
End Function
```

## <a name="complete-example"></a>Kompletní příklad

Následující kód je kompletní příklad, který obsahuje funkci `XForm`. Obsahuje několik typických použití tohoto typu transformace:

```vb
Imports System
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports System.Xml
Imports System.Xml.Linq

Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    ' Build a transformed XML tree per the annotations.
    Function XForm(ByVal source As XElement) As XElement
        If source.Annotation(Of XElement)() IsNot Nothing Then
            Dim anno As XElement = source.Annotation(Of XElement)()
            Return _
                <<%= anno.Name.ToString() %>>
                    <%= anno.Attributes() %>
                    <%= anno.Nodes().Select(Function(n As XNode) _
                        GetSubNodes(n, source)) %>
                </>
        Else
            Return _
                <<%= source.Name %>>
                    <%= source.Attributes() %>
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
                </>
        End If
    End Function

    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
        Dim annoEl As XElement = TryCast(n, XElement)
        If annoEl IsNot Nothing Then
            If annoEl.Name = at Then
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
            End If
        End If
        Return n
    End Function

    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
        Dim e2 As XElement = TryCast(n2, XElement)
        If e2 Is Nothing Then
            Return n2
        Else
            Return XForm(e2)
        End If
    End Function

    Sub Main()
        Dim root As XElement = _
<Root Att1='123'>
    <!--A comment-->
    <Child>1</Child>
    <Child>2</Child>
    <Other>
        <GC>3</GC>
        <GC>4</GC>
    </Other>
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
    <AnUnchangedElement>42</AnUnchangedElement>
</Root>

        ' Each of the following serves the same semantic purpose as
        ' XSLT templates and sequence constructors.

        ' Replace Child with NewChild.
        For Each el In root.<Child>
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)
        Next

        ' Replace first GC with GrandChild, add an attribute.
        For Each el In root...<GC>.Take(1)
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)
        Next

        ' Replace Other with NewOther, add new child elements around original content.
        For Each el In root.<Other>
            el.AddAnnotation( _
                <NewOther>
                    <MyNewChild>1</MyNewChild>
                    <<%= at %>></>
                    <ChildThatComesAfter/>
                </NewOther>)
        Next

        ' Change name of element that has mixed content.
        root...<SomeMixedContent>(0).AddAnnotation( _
                <MixedContent><<%= at %>></></MixedContent>)

        ' Replace <b> with <Bold>.
        For Each el In root...<b>
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)
        Next

        ' Replace <i> with <Italic>.
        For Each el In root...<i>
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)
        Next

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(root)
        Console.WriteLine(vbNewLine)
        Dim newRoot As XElement = XForm(root)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newRoot)
    End Sub
End Module 
```

Tento příklad vytvoří následující výstup:

```console
Before Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <Child>1</Child>
  <Child>2</Child>
  <Other>
    <GC>3</GC>
    <GC>4</GC>
  </Other>
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>

After Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <NewChild>1</NewChild>
  <NewChild>2</NewChild>
  <NewOther>
    <MyNewChild>1</MyNewChild>
    <GrandChild ANewAttribute="999">3</GrandChild>
    <GC>4</GC>
    <ChildThatComesAfter />
  </NewOther>
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>
```

## <a name="see-also"></a>Viz také:

- [Rozšířené programování LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
