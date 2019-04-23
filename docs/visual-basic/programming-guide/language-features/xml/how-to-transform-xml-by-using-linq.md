---
title: 'Postupy: Transformace XML pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: c34d3988c89e0ce07676e9181200fc039010b50a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324980"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="19dd1-102">Postupy: Transformace XML pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19dd1-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="19dd1-103">[Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md) usnadňují přečíst XML z jednoho zdroje a transformovat ho do nového formátu XML.</span><span class="sxs-lookup"><span data-stu-id="19dd1-103">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="19dd1-104">Můžete využívat dotazy LINQ načítat obsah, který umožňuje transformovat nebo změnit obsah v existující dokument na nový formát XML.</span><span class="sxs-lookup"><span data-stu-id="19dd1-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>  
  
 <span data-ttu-id="19dd1-105">V příkladu v tomto tématu transformuje obsah ze zdrojového dokumentu XML do formátu HTML, které lze zobrazit v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="19dd1-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a><span data-ttu-id="19dd1-106">K transformaci dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="19dd1-106">To transform an XML document</span></span>  
  
1. <span data-ttu-id="19dd1-107">V sadě Visual Studio vytvořte nový projekt v jazyce Visual Basic **konzolovou aplikaci** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="19dd1-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>  
  
2. <span data-ttu-id="19dd1-108">Poklikejte na soubor Module1.vb vytvořen v projektu a upravte kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="19dd1-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="19dd1-109">Přidejte následující kód, který `Sub Main` z `Module1` modulu.</span><span class="sxs-lookup"><span data-stu-id="19dd1-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="19dd1-110">Tento kód vytvoří zdrojovém dokumentu XML jako <xref:System.Xml.Linq.XDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="19dd1-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
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
  
     <span data-ttu-id="19dd1-111">[Postupy: Načtení XML ze souboru, řetězce nebo Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span><span class="sxs-lookup"><span data-stu-id="19dd1-111">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span></span>  
  
3. <span data-ttu-id="19dd1-112">Za kód k vytvoření zdrojového dokumentu XML, přidejte následující kód k načtení všech \<knihy > prvky z objektu a transformují je na dokument HTML.</span><span class="sxs-lookup"><span data-stu-id="19dd1-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="19dd1-113">Seznam \<knihy > prvků je vytvořena pomocí dotaz LINQ, který vrátí kolekci <xref:System.Xml.Linq.XElement> objektů, které obsahují kód HTML pro transformovaná.</span><span class="sxs-lookup"><span data-stu-id="19dd1-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="19dd1-114">Vložené výrazy můžete použít pro převedení hodnot ze zdrojového dokumentu v novém formátu XML.</span><span class="sxs-lookup"><span data-stu-id="19dd1-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>  
  
     <span data-ttu-id="19dd1-115">Výsledný dokumentu HTML je zapsána do souboru s použitím <xref:System.Xml.Linq.XElement.Save%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="19dd1-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>  
  
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
  
4. <span data-ttu-id="19dd1-116">Po `Sub Main` z `Module1`, přidejte novou metodu (`Sub`) k transformaci \<popis > uzlu na zadaném formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="19dd1-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="19dd1-117">Tato metoda je volána kód v předchozím kroku a používá k zachování formát \<popis > elementy.</span><span class="sxs-lookup"><span data-stu-id="19dd1-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>  
  
     <span data-ttu-id="19dd1-118">Tato metoda nahrazuje dílčí prvky \<popis > element s HTML.</span><span class="sxs-lookup"><span data-stu-id="19dd1-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="19dd1-119">`ReplaceWith` Metoda se používá k zachování umístění podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="19dd1-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="19dd1-120">Transformovaný obsah \<popis > element je součástí HTML odstavec (\<p >) element.</span><span class="sxs-lookup"><span data-stu-id="19dd1-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="19dd1-121"><xref:System.Xml.Linq.XContainer.Nodes%2A> Vlastnost se používá k načtení transformovaný obsah \<popis > element.</span><span class="sxs-lookup"><span data-stu-id="19dd1-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="19dd1-122">Tím se zajistí, že dílčí prvky jsou součástí převedeného obsahu.</span><span class="sxs-lookup"><span data-stu-id="19dd1-122">This ensures that sub-elements are included in the transformed content.</span></span>  
  
     <span data-ttu-id="19dd1-123">Přidejte následující kód za `Sub Main` z `Module1`.</span><span class="sxs-lookup"><span data-stu-id="19dd1-123">Add the following code after `Sub Main` of `Module1`.</span></span>  
  
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
  
5. <span data-ttu-id="19dd1-124">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="19dd1-124">Save your changes.</span></span>  
  
6. <span data-ttu-id="19dd1-125">Stisknutím klávesy F5 spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="19dd1-125">Press F5 to run the code.</span></span> <span data-ttu-id="19dd1-126">Výsledná uložit dokument bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="19dd1-126">The resulting saved document will resemble the following:</span></span>  
  
    ```  
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
  
## <a name="see-also"></a><span data-ttu-id="19dd1-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19dd1-127">See also</span></span>

- [<span data-ttu-id="19dd1-128">Literály XML</span><span class="sxs-lookup"><span data-stu-id="19dd1-128">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="19dd1-129">Manipulace s kódem XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19dd1-129">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="19dd1-130">XML</span><span class="sxs-lookup"><span data-stu-id="19dd1-130">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="19dd1-131">Postupy: Načtení XML ze souboru, řetězce nebo Stream</span><span class="sxs-lookup"><span data-stu-id="19dd1-131">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="19dd1-132">LINQ</span><span class="sxs-lookup"><span data-stu-id="19dd1-132">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="19dd1-133">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19dd1-133">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
