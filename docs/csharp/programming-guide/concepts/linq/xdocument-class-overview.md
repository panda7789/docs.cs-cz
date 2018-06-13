---
title: Přehled třídy XDocument (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 999d570725acbf328858b0ef6c69f709317f10fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333346"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="e16a2-102">Přehled třídy XDocument (C#)</span><span class="sxs-lookup"><span data-stu-id="e16a2-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="e16a2-103">Toto téma představuje <xref:System.Xml.Linq.XDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="e16a2-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="e16a2-104">Přehled třídy XDocument</span><span class="sxs-lookup"><span data-stu-id="e16a2-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="e16a2-105"><xref:System.Xml.Linq.XDocument> Třída obsahuje informace potřebné pro platný dokument XML.</span><span class="sxs-lookup"><span data-stu-id="e16a2-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="e16a2-106">To zahrnuje deklarace XML, zpracování pokyny a komentáře.</span><span class="sxs-lookup"><span data-stu-id="e16a2-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="e16a2-107">Všimněte si, že budete muset vytvořit <xref:System.Xml.Linq.XDocument> objekty, pokud potřebujete konkrétní funkce poskytované službou <xref:System.Xml.Linq.XDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="e16a2-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="e16a2-108">V mnoha případech může spolupracovat přímo s <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e16a2-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e16a2-109">Práce přímo s <xref:System.Xml.Linq.XElement> je jednodušší programovací model.</span><span class="sxs-lookup"><span data-stu-id="e16a2-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="e16a2-110"><xref:System.Xml.Linq.XDocument> odvozená z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="e16a2-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="e16a2-111">Proto může obsahovat podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="e16a2-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="e16a2-112">Ale <xref:System.Xml.Linq.XDocument> objekty může mít pouze jednu podřízenou <xref:System.Xml.Linq.XElement> uzlu.</span><span class="sxs-lookup"><span data-stu-id="e16a2-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="e16a2-113">Tento údaj zohledňuje standardní XML, že v dokumentu XML může existovat jenom jeden kořenový element.</span><span class="sxs-lookup"><span data-stu-id="e16a2-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="e16a2-114">Součástí XDocument</span><span class="sxs-lookup"><span data-stu-id="e16a2-114">Components of XDocument</span></span>  
 <span data-ttu-id="e16a2-115"><xref:System.Xml.Linq.XDocument> Může obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="e16a2-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="e16a2-116">Jeden <xref:System.Xml.Linq.XDeclaration> objektu.</span><span class="sxs-lookup"><span data-stu-id="e16a2-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="e16a2-117"><xref:System.Xml.Linq.XDeclaration> Umožňuje určit příslušné části deklarace XML: verze XML, kódování dokumentu, a jestli je samostatné dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e16a2-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="e16a2-118">Jeden <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="e16a2-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="e16a2-119">Toto je kořenový uzel dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e16a2-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="e16a2-120">Libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objekty.</span><span class="sxs-lookup"><span data-stu-id="e16a2-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="e16a2-121">Zpracování instrukcí komunikuje informace, které aplikace, která zpracovává soubor XML.</span><span class="sxs-lookup"><span data-stu-id="e16a2-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="e16a2-122">Libovolný počet <xref:System.Xml.Linq.XComment> objekty.</span><span class="sxs-lookup"><span data-stu-id="e16a2-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="e16a2-123">Komentáře bude na stejné úrovni pro kořenový element.</span><span class="sxs-lookup"><span data-stu-id="e16a2-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="e16a2-124"><xref:System.Xml.Linq.XComment> Objektu nemůže být prvním argumentem v seznamu, protože není platný pro dokument XML a začněte komentář.</span><span class="sxs-lookup"><span data-stu-id="e16a2-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="e16a2-125">Jeden <xref:System.Xml.Linq.XDocumentType> pro DTD.</span><span class="sxs-lookup"><span data-stu-id="e16a2-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="e16a2-126">Při serializaci <xref:System.Xml.Linq.XDocument>i v případě `XDocument.Declaration` je `null`, výstup bude mít deklarace XML, pokud má zapisovač `Writer.Settings.OmitXmlDeclaration` nastavena na `false` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e16a2-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="e16a2-127">Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví na verzi "1.0" a kódování "znakové sady utf-8".</span><span class="sxs-lookup"><span data-stu-id="e16a2-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="e16a2-128">Pomocí XElement bez XDocument</span><span class="sxs-lookup"><span data-stu-id="e16a2-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="e16a2-129">Jak už jsme zmínili, <xref:System.Xml.Linq.XElement> třída je hlavní třídy ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e16a2-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="e16a2-130">V mnoha případech aplikace nebude vyžadovat vytvoření dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e16a2-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="e16a2-131">Pomocí <xref:System.Xml.Linq.XElement> třídu, můžete vytvořit strom XML, do ní přidejte další XML stromy, upravit stromu XML a uložte ho.</span><span class="sxs-lookup"><span data-stu-id="e16a2-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="e16a2-132">Pomocí XDocument</span><span class="sxs-lookup"><span data-stu-id="e16a2-132">Using XDocument</span></span>  
 <span data-ttu-id="e16a2-133">K vytvoření <xref:System.Xml.Linq.XDocument>, použít funkční konstrukce, stejně jako můžete vytvořit <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="e16a2-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="e16a2-134">Následující kód vytvoří <xref:System.Xml.Linq.XDocument> objektu a jeho přidružených obsažené objekty.</span><span class="sxs-lookup"><span data-stu-id="e16a2-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
```  
  
 <span data-ttu-id="e16a2-135">Při kontrole souboru test.xml, získáte tento výstup:</span><span class="sxs-lookup"><span data-stu-id="e16a2-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="e16a2-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="e16a2-136">See Also</span></span>  
 [<span data-ttu-id="e16a2-137">Technologie LINQ to XML přehled programování (C#)</span><span class="sxs-lookup"><span data-stu-id="e16a2-137">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
