---
title: Přehled třídy XDocument (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 9a2b2e7490116cfd7ff3cff783a4a3a985a39d0a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595341"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="ccfb0-102">Přehled třídy XDocument (C#)</span><span class="sxs-lookup"><span data-stu-id="ccfb0-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="ccfb0-103">Toto téma představuje <xref:System.Xml.Linq.XDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="ccfb0-104">Přehled třídy XDocument</span><span class="sxs-lookup"><span data-stu-id="ccfb0-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="ccfb0-105"><xref:System.Xml.Linq.XDocument> Třída obsahuje informace potřebné pro platný dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="ccfb0-106">To zahrnuje deklarace XML, zpracování pokyny a komentáře.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="ccfb0-107">Všimněte si, že budete muset vytvořit <xref:System.Xml.Linq.XDocument> objektů, pokud potřebujete konkrétní funkce poskytované službou <xref:System.Xml.Linq.XDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="ccfb0-108">V mnoha případech platí, může spolupracovat přímo s <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="ccfb0-109">Práce přímo s <xref:System.Xml.Linq.XElement> je jednodušší programovací model.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="ccfb0-110"><xref:System.Xml.Linq.XDocument> je odvozen od <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="ccfb0-111">Proto může obsahovat podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="ccfb0-112">Ale <xref:System.Xml.Linq.XDocument> objekty mohou mít pouze jeden podřízený prvek <xref:System.Xml.Linq.XElement> uzlu.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="ccfb0-113">To odpovídá standardu XML mohou být pouze jeden kořenový element v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="ccfb0-114">Součástí XDocument</span><span class="sxs-lookup"><span data-stu-id="ccfb0-114">Components of XDocument</span></span>  
 <span data-ttu-id="ccfb0-115"><xref:System.Xml.Linq.XDocument> Může obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="ccfb0-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="ccfb0-116">Jeden <xref:System.Xml.Linq.XDeclaration> objektu.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="ccfb0-117"><xref:System.Xml.Linq.XDeclaration> Umožňuje určit, které jsou relevantní části deklarace XML: XML version, kódování dokumentu, a zda je samostatný dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="ccfb0-118">Jeden <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="ccfb0-119">Toto je kořenový uzel dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="ccfb0-120">Libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objekty.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="ccfb0-121">Instrukce pro zpracování komunikuje informace k aplikaci, která zpracovává XML.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="ccfb0-122">Libovolný počet <xref:System.Xml.Linq.XComment> objekty.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="ccfb0-123">Komentáře se na stejné úrovni jako kořenový element.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="ccfb0-124"><xref:System.Xml.Linq.XComment> Objektu nemůže být prvním argumentem v seznamu, protože není platný pro začínat komentář dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="ccfb0-125">Jeden <xref:System.Xml.Linq.XDocumentType> pro DTD.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="ccfb0-126">Při serializaci <xref:System.Xml.Linq.XDocument>i v případě `XDocument.Declaration` je `null`, výstup bude mít deklarace XML, pokud má modul pro zápis `Writer.Settings.OmitXmlDeclaration` nastavena na `false` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ccfb0-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="ccfb0-127">Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví verzi "1.0" a nastaví kódování na "utf-8".</span><span class="sxs-lookup"><span data-stu-id="ccfb0-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="ccfb0-128">Pomocí XElement bez XDocument</span><span class="sxs-lookup"><span data-stu-id="ccfb0-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="ccfb0-129">Jak už jsme zmínili, <xref:System.Xml.Linq.XElement> třída je hlavní třída v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="ccfb0-130">V mnoha případech se vaše aplikace nebude vyžadovat vytvoření dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="ccfb0-131">S použitím <xref:System.Xml.Linq.XElement> třídy, můžete vytvořit stromu XML, k němu přidat další stromů XML, upravte stromu XML a uložit jej.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="ccfb0-132">Pomocí XDocument</span><span class="sxs-lookup"><span data-stu-id="ccfb0-132">Using XDocument</span></span>  
 <span data-ttu-id="ccfb0-133">K vytvoření <xref:System.Xml.Linq.XDocument>, použijte funkční konstrukce, stejně jako máte k sestavení kompletních <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="ccfb0-134">Následující kód vytvoří <xref:System.Xml.Linq.XDocument> objektu a jeho přidruženého obsažené objekty.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="ccfb0-135">Při zkoumání souboru test.xml, získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ccfb0-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ccfb0-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccfb0-136">See also</span></span>

- [<span data-ttu-id="ccfb0-137">Přehled LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="ccfb0-137">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
