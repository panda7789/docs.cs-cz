---
title: XDocument – Přehled třídy (C#)
description: Třída XDocument v jazyce C# obsahuje informace potřebné pro platný dokument XML, včetně deklarace XML, instrukcí pro zpracování a komentářů.
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 6d522cef25e99e4a5ea54e644855c8dfa7a05f4a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302188"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="fdc5b-103">XDocument – Přehled třídy (C#)</span><span class="sxs-lookup"><span data-stu-id="fdc5b-103">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="fdc5b-104">Toto téma představuje <xref:System.Xml.Linq.XDocument> třídu.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-104">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="fdc5b-105">Přehled třídy XDocument</span><span class="sxs-lookup"><span data-stu-id="fdc5b-105">Overview of the XDocument class</span></span>  
 <span data-ttu-id="fdc5b-106"><xref:System.Xml.Linq.XDocument>Třída obsahuje informace potřebné pro platný dokument XML.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-106">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="fdc5b-107">To zahrnuje deklarace XML, instrukce pro zpracování a komentáře.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-107">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="fdc5b-108">Všimněte si, že je třeba vytvořit <xref:System.Xml.Linq.XDocument> objekty pouze v případě, že požadujete konkrétní funkce poskytované <xref:System.Xml.Linq.XDocument> třídou.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-108">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="fdc5b-109">V mnoha případech můžete pracovat přímo s <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="fdc5b-109">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="fdc5b-110">Práce přímo s nástrojem <xref:System.Xml.Linq.XElement> je jednodušší programovací model.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-110">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="fdc5b-111"><xref:System.Xml.Linq.XDocument>je odvozen z <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="fdc5b-111"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="fdc5b-112">Proto může obsahovat podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-112">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="fdc5b-113">Nicméně <xref:System.Xml.Linq.XDocument> objekty mohou mít pouze jeden podřízený <xref:System.Xml.Linq.XElement> uzel.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-113">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="fdc5b-114">To odráží standard XML, že v dokumentu XML může být pouze jeden kořenový element.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-114">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="fdc5b-115">Komponenty XDocument</span><span class="sxs-lookup"><span data-stu-id="fdc5b-115">Components of XDocument</span></span>  
 <span data-ttu-id="fdc5b-116"><xref:System.Xml.Linq.XDocument>Může obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="fdc5b-116">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="fdc5b-117">Jeden <xref:System.Xml.Linq.XDeclaration> objekt.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-117">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="fdc5b-118"><xref:System.Xml.Linq.XDeclaration>umožňuje zadat relevantní části deklarace XML: verze XML, kódování dokumentu a zda je dokument XML samostatný.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-118"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="fdc5b-119">Jeden <xref:System.Xml.Linq.XElement> objekt.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-119">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="fdc5b-120">Toto je kořenový uzel dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-120">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="fdc5b-121">Libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objektů.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-121">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="fdc5b-122">Instrukce pro zpracování sděluje informace aplikaci, která zpracovává XML.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-122">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="fdc5b-123">Libovolný počet <xref:System.Xml.Linq.XComment> objektů.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-123">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="fdc5b-124">Komentáře budou na stejné úrovni jako kořenový element.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-124">The comments will be siblings to the root element.</span></span> <span data-ttu-id="fdc5b-125"><xref:System.Xml.Linq.XComment>Objekt nemůže být prvním argumentem v seznamu, protože není platný pro dokument XML, aby začínat komentářem.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-125">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="fdc5b-126">Jednu <xref:System.Xml.Linq.XDocumentType> pro DTD.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-126">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="fdc5b-127">Při serializaci <xref:System.Xml.Linq.XDocument> , i když `XDocument.Declaration` je `null` , výstup bude obsahovat deklaraci XML, pokud zapisovač je `Writer.Settings.OmitXmlDeclaration` nastaven na `false` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="fdc5b-127">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="fdc5b-128">Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví verzi na "1,0" a nastaví kódování na UTF-8.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-128">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="fdc5b-129">Použití XElement bez XDocument</span><span class="sxs-lookup"><span data-stu-id="fdc5b-129">Using XElement without XDocument</span></span>  
 <span data-ttu-id="fdc5b-130">Jak už jsme uvedli, <xref:System.Xml.Linq.XElement> Třída je hlavní třídou v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovacím rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-130">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="fdc5b-131">V mnoha případech aplikace nebude vyžadovat vytvoření dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-131">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="fdc5b-132">Pomocí <xref:System.Xml.Linq.XElement> třídy můžete vytvořit strom XML, přidat do něj další stromy XML, upravit strom XML a uložit jej.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-132">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="fdc5b-133">Použití XDocument</span><span class="sxs-lookup"><span data-stu-id="fdc5b-133">Using XDocument</span></span>  
 <span data-ttu-id="fdc5b-134">Chcete-li vytvořit <xref:System.Xml.Linq.XDocument> , použijte funkční konstrukci stejným způsobem jako při vytváření <xref:System.Xml.Linq.XElement> objektů.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-134">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="fdc5b-135">Následující kód vytvoří <xref:System.Xml.Linq.XDocument> objekt a jeho přidružené objekty v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="fdc5b-135">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="fdc5b-136">Po prohlédnutí test.xml souboru se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fdc5b-136">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fdc5b-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdc5b-137">See also</span></span>

- [<span data-ttu-id="fdc5b-138">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fdc5b-138">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
