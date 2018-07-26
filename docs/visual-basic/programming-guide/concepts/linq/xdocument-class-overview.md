---
title: Přehled třídy XDocument (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 98ab095d67add2375eaf912ade71114c022b2ebb
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220945"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="a019f-102">Přehled třídy XDocument (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a019f-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="a019f-103">Toto téma představuje <xref:System.Xml.Linq.XDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="a019f-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="a019f-104">Přehled třídy XDocument</span><span class="sxs-lookup"><span data-stu-id="a019f-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="a019f-105"><xref:System.Xml.Linq.XDocument> Třída obsahuje informace potřebné pro platný dokument XML.</span><span class="sxs-lookup"><span data-stu-id="a019f-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="a019f-106">To zahrnuje deklarace XML, zpracování pokyny a komentáře.</span><span class="sxs-lookup"><span data-stu-id="a019f-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="a019f-107">Všimněte si, že budete muset vytvořit <xref:System.Xml.Linq.XDocument> objektů, pokud potřebujete konkrétní funkce poskytované službou <xref:System.Xml.Linq.XDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="a019f-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="a019f-108">V mnoha případech platí, může spolupracovat přímo s <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a019f-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="a019f-109">Práce přímo s <xref:System.Xml.Linq.XElement> je jednodušší programovací model.</span><span class="sxs-lookup"><span data-stu-id="a019f-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="a019f-110"><xref:System.Xml.Linq.XDocument> je odvozen od <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="a019f-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="a019f-111">Proto může obsahovat podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="a019f-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="a019f-112">Ale <xref:System.Xml.Linq.XDocument> objekty mohou mít pouze jeden podřízený prvek <xref:System.Xml.Linq.XElement> uzlu.</span><span class="sxs-lookup"><span data-stu-id="a019f-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="a019f-113">To odpovídá standardu XML mohou být pouze jeden kořenový element v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a019f-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="a019f-114">Součástí XDocument</span><span class="sxs-lookup"><span data-stu-id="a019f-114">Components of XDocument</span></span>  
 <span data-ttu-id="a019f-115"><xref:System.Xml.Linq.XDocument> Může obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="a019f-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="a019f-116">Jeden <xref:System.Xml.Linq.XDeclaration> objektu.</span><span class="sxs-lookup"><span data-stu-id="a019f-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="a019f-117"><xref:System.Xml.Linq.XDeclaration> Umožňuje určit, které jsou relevantní části deklarace XML: XML version, kódování dokumentu, a zda je samostatný dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a019f-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="a019f-118">Jeden <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="a019f-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="a019f-119">Toto je kořenový uzel dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a019f-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="a019f-120">Libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objekty.</span><span class="sxs-lookup"><span data-stu-id="a019f-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="a019f-121">Instrukce pro zpracování komunikuje informace k aplikaci, která zpracovává XML.</span><span class="sxs-lookup"><span data-stu-id="a019f-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="a019f-122">Libovolný počet <xref:System.Xml.Linq.XComment> objekty.</span><span class="sxs-lookup"><span data-stu-id="a019f-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="a019f-123">Komentáře se na stejné úrovni jako kořenový element.</span><span class="sxs-lookup"><span data-stu-id="a019f-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="a019f-124"><xref:System.Xml.Linq.XComment> Objektu nemůže být prvním argumentem v seznamu, protože není platný pro začínat komentář dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a019f-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="a019f-125">Jeden <xref:System.Xml.Linq.XDocumentType> pro DTD.</span><span class="sxs-lookup"><span data-stu-id="a019f-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="a019f-126">Při serializaci <xref:System.Xml.Linq.XDocument>i v případě `XDocument.Declaration` je `null`, výstup bude mít deklarace XML, pokud má modul pro zápis `Writer.Settings.OmitXmlDeclaration` nastavena na `false` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a019f-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="a019f-127">Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví verzi "1.0" a nastaví kódování na "utf-8".</span><span class="sxs-lookup"><span data-stu-id="a019f-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="a019f-128">Pomocí XElement bez XDocument</span><span class="sxs-lookup"><span data-stu-id="a019f-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="a019f-129">Jak už jsme zmínili, <xref:System.Xml.Linq.XElement> třída je hlavní třída v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a019f-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="a019f-130">V mnoha případech se vaše aplikace nebude vyžadovat vytvoření dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a019f-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="a019f-131">S použitím <xref:System.Xml.Linq.XElement> třídy, můžete vytvořit stromu XML, k němu přidat další stromů XML, upravte stromu XML a uložit jej.</span><span class="sxs-lookup"><span data-stu-id="a019f-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="a019f-132">Pomocí XDocument</span><span class="sxs-lookup"><span data-stu-id="a019f-132">Using XDocument</span></span>  
 <span data-ttu-id="a019f-133">K vytvoření <xref:System.Xml.Linq.XDocument>, použijte funkční konstrukce, stejně jako máte k sestavení kompletních <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="a019f-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="a019f-134">Následující kód vytvoří <xref:System.Xml.Linq.XDocument> objektu a jeho přidruženého obsažené objekty.</span><span class="sxs-lookup"><span data-stu-id="a019f-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
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
doc.Save("test.xml")  
```  
  
 <span data-ttu-id="a019f-135">Při zkoumání souboru test.xml, získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a019f-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a019f-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="a019f-136">See Also</span></span>  
 [<span data-ttu-id="a019f-137">Přehled LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a019f-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
