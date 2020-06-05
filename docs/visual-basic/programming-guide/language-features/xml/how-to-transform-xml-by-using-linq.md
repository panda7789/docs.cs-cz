---
title: 'Postupy: Transformace XML pomocí LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: dab394ec45567589e002b5d2ac76ec19fb0f76c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374878"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="9159a-102">Postupy: Transformace XML pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9159a-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="9159a-103">[Literály XML](../../../language-reference/xml-literals/index.md) usnadňují čtení XML z jednoho zdroje a jejich transformaci do nového formátu XML.</span><span class="sxs-lookup"><span data-stu-id="9159a-103">[XML Literals](../../../language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="9159a-104">Můžete využít výhod dotazů LINQ k načtení obsahu pro transformaci nebo změnu obsahu v existujícím dokumentu do nového formátu XML.</span><span class="sxs-lookup"><span data-stu-id="9159a-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>

<span data-ttu-id="9159a-105">Příklad v tomto tématu transformuje obsah ze zdrojového dokumentu XML do HTML pro zobrazení v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9159a-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a><span data-ttu-id="9159a-106">Transformace dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="9159a-106">To transform an XML document</span></span>

1. <span data-ttu-id="9159a-107">V aplikaci Visual Studio vytvořte nový projekt Visual Basic v šabloně projektu **Konzolová aplikace** .</span><span class="sxs-lookup"><span data-stu-id="9159a-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>

2. <span data-ttu-id="9159a-108">Dvojím kliknutím na soubor Module1. vb, který jste vytvořili v projektu, upravte kód Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9159a-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="9159a-109">Do modulu přidejte následující kód `Sub Main` `Module1` .</span><span class="sxs-lookup"><span data-stu-id="9159a-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="9159a-110">Tento kód vytvoří zdrojový dokument XML jako <xref:System.Xml.Linq.XDocument> objekt.</span><span class="sxs-lookup"><span data-stu-id="9159a-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>

    ```vb
    Dim catalog =
      <?xml version="1.0"?>
        <Catalog>
          <Book id="bk101">
            <Author>Garghentini, Davide</Author>
            <Title>XML Developer's Guide</Title>
            <Price>44.95</Price>
            <Description>
              An in-depth look at creating applications
              with <technology>XML</technology>. For
              <audience>beginners</audience> or
              <audience>advanced</audience> developers.
            </Description>
          </Book>
          <Book id="bk331">
            <Author>Spencer, Phil</Author>
            <Title>Developing Applications with Visual Basic .NET</Title>
            <Price>45.95</Price>
            <Description>
              Get the expert insights, practical code samples,
              and best practices you need
              to advance your expertise with <technology>Visual
              Basic .NET</technology>.
              Learn how to create faster, more reliable applications
              based on professional,
              pragmatic guidance by today's top <audience>developers</audience>.
            </Description>
          </Book>
        </Catalog>
    ```

     <span data-ttu-id="9159a-111">[Postupy: načtení XML ze souboru, řetězce nebo datového proudu](how-to-load-xml-from-a-file-string-or-stream.md).</span><span class="sxs-lookup"><span data-stu-id="9159a-111">[How to: Load XML from a File, String, or Stream](how-to-load-xml-from-a-file-string-or-stream.md).</span></span>

3. <span data-ttu-id="9159a-112">Po kódu pro vytvoření zdrojového dokumentu XML přidejte následující kód, který načte všechny \<Book> prvky z objektu a převede je na dokument HTML.</span><span class="sxs-lookup"><span data-stu-id="9159a-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="9159a-113">Seznam \<Book> elementů je vytvořen pomocí dotazu LINQ, který vrací kolekci <xref:System.Xml.Linq.XElement> objektů, které obsahují transformovaný kód HTML.</span><span class="sxs-lookup"><span data-stu-id="9159a-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="9159a-114">Vložené výrazy můžete použít k umístění hodnot ze zdrojového dokumentu do nového formátu XML.</span><span class="sxs-lookup"><span data-stu-id="9159a-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>

     <span data-ttu-id="9159a-115">Výsledný dokument HTML je zapsán do souboru pomocí <xref:System.Xml.Linq.XElement.Save%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9159a-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>

    ```vb
    Dim htmlOutput =
      <html>
        <body>
          <%= From book In catalog.<Catalog>.<Book>
              Select <div>
                       <h1><%= book.<Title>.Value %></h1>
                       <h3><%= "By " & book.<Author>.Value %></h3>
                        <h3><%= "Price = " & book.<Price>.Value %></h3>
                        <h2>Description</h2>
                        <%= TransformDescription(book.<Description>(0)) %>
                        <hr/>
                      </div> %>
        </body>
      </html>

    htmlOutput.Save("BookDescription.html")
    ```

4. <span data-ttu-id="9159a-116">Po `Sub Main` `Module1` přidejte novou metodu ( `Sub` ) pro transformaci \<Description> uzlu do zadaného formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="9159a-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="9159a-117">Tato metoda je volána kódem v předchozím kroku a slouží k zachování formátu \<Description> prvků.</span><span class="sxs-lookup"><span data-stu-id="9159a-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>

     <span data-ttu-id="9159a-118">Tato metoda nahrazuje dílčí prvky \<Description> elementu pomocí HTML.</span><span class="sxs-lookup"><span data-stu-id="9159a-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="9159a-119">`ReplaceWith`Metoda se používá k zachování umístění dílčích prvků.</span><span class="sxs-lookup"><span data-stu-id="9159a-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="9159a-120">Transformovaný obsah \<Description> elementu je obsažen v elementu odstavce () jazyka HTML \<p> .</span><span class="sxs-lookup"><span data-stu-id="9159a-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="9159a-121"><xref:System.Xml.Linq.XContainer.Nodes%2A>Vlastnost slouží k načtení transformovanýho obsahu \<Description> elementu.</span><span class="sxs-lookup"><span data-stu-id="9159a-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="9159a-122">Tím se zajistí, že dílčí prvky budou zahrnuty v transformovaným obsahu.</span><span class="sxs-lookup"><span data-stu-id="9159a-122">This ensures that sub-elements are included in the transformed content.</span></span>

     <span data-ttu-id="9159a-123">Přidejte následující kód za `Sub Main` `Module1` .</span><span class="sxs-lookup"><span data-stu-id="9159a-123">Add the following code after `Sub Main` of `Module1`.</span></span>

    ```vb
    Public Function TransformDescription(ByVal desc As XElement) As XElement

      ' Replace <technology> elements with <b>.
      Dim content = (From element In desc...<technology>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)
        Next
      End If

      ' Replace <audience> elements with <i>.
      content = (From element In desc...<audience>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)
        Next
      End If

      ' Return the updated contents of the <Description> element.
      Return <p><%= desc.Nodes %></p>
    End Function
    ```

5. <span data-ttu-id="9159a-124">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="9159a-124">Save your changes.</span></span>

6. <span data-ttu-id="9159a-125">Stisknutím klávesy F5 spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="9159a-125">Press F5 to run the code.</span></span> <span data-ttu-id="9159a-126">Výsledný uložený dokument bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="9159a-126">The resulting saved document will resemble the following:</span></span>

    ```html
    <?xml version="1.0"?>
    <html>
      <body>
        <div>
          <h1>XML Developer's Guide</h1>
          <h3>By Garghentini, Davide</h3>
          <h3>Price = 44.95</h3>
          <h2>Description</h2>
          <p>
            An in-depth look at creating applications
            with <b>XML</b>. For
            <i>beginners</i> or
            <i>advanced</i> developers.
          </p>
          <hr />
        </div>
        <div>
          <h1>Developing Applications with Visual Basic .NET</h1>
          <h3>By Spencer, Phil</h3>
          <h3>Price = 45.95</h3>
          <h2>Description</h2>
          <p>
            Get the expert insights, practical code
            samples, and best practices you need
            to advance your expertise with <b>Visual
            Basic .NET</b>. Learn how to create faster,
            more reliable applications based on
            professional, pragmatic guidance by today's
            top <i>developers</i>.
          </p>
          <hr />
        </div>
      </body>
    </html>
    ```

## <a name="see-also"></a><span data-ttu-id="9159a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9159a-127">See also</span></span>

- [<span data-ttu-id="9159a-128">Literály XML</span><span class="sxs-lookup"><span data-stu-id="9159a-128">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="9159a-129">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9159a-129">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="9159a-130">XML</span><span class="sxs-lookup"><span data-stu-id="9159a-130">XML</span></span>](index.md)
- [<span data-ttu-id="9159a-131">Postupy: Načtení XML ze souboru, řetězce nebo proudu</span><span class="sxs-lookup"><span data-stu-id="9159a-131">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="9159a-132">LINQ</span><span class="sxs-lookup"><span data-stu-id="9159a-132">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="9159a-133">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9159a-133">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
