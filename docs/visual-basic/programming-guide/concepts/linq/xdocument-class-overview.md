---
title: Přehled třídy XDocument
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: cbc1ccca53978da07f31c0ba7e54eca9f06b0e72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349294"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="1397c-102">XDocument – Přehled třídy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1397c-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="1397c-103">Toto téma představuje třídu <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="1397c-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="1397c-104">Přehled třídy XDocument</span><span class="sxs-lookup"><span data-stu-id="1397c-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="1397c-105">Třída <xref:System.Xml.Linq.XDocument> obsahuje informace potřebné pro platný dokument XML.</span><span class="sxs-lookup"><span data-stu-id="1397c-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="1397c-106">To zahrnuje deklarace XML, instrukce pro zpracování a komentáře.</span><span class="sxs-lookup"><span data-stu-id="1397c-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="1397c-107">Všimněte si, že je nutné vytvořit <xref:System.Xml.Linq.XDocument> objekty pouze v případě, že požadujete konkrétní funkčnost poskytovanou <xref:System.Xml.Linq.XDocument>ou třídou.</span><span class="sxs-lookup"><span data-stu-id="1397c-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="1397c-108">V mnoha případech můžete pracovat přímo s <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1397c-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="1397c-109">Práce přímo s <xref:System.Xml.Linq.XElement> je jednodušší programovací model.</span><span class="sxs-lookup"><span data-stu-id="1397c-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="1397c-110"><xref:System.Xml.Linq.XDocument> jsou odvozeny z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="1397c-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="1397c-111">Proto může obsahovat podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="1397c-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="1397c-112"><xref:System.Xml.Linq.XDocument> objektů však může mít pouze jeden podřízený <xref:System.Xml.Linq.XElement> uzel.</span><span class="sxs-lookup"><span data-stu-id="1397c-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="1397c-113">To odráží standard XML, že v dokumentu XML může být pouze jeden kořenový element.</span><span class="sxs-lookup"><span data-stu-id="1397c-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="1397c-114">Komponenty XDocument</span><span class="sxs-lookup"><span data-stu-id="1397c-114">Components of XDocument</span></span>  
 <span data-ttu-id="1397c-115"><xref:System.Xml.Linq.XDocument> může obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="1397c-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="1397c-116">Jeden objekt <xref:System.Xml.Linq.XDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="1397c-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="1397c-117"><xref:System.Xml.Linq.XDeclaration> umožňuje zadat relevantní části deklarace XML: verze XML, kódování dokumentu a zda je dokument XML samostatný.</span><span class="sxs-lookup"><span data-stu-id="1397c-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="1397c-118">Jeden objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1397c-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="1397c-119">Toto je kořenový uzel dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="1397c-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="1397c-120">Libovolný počet objektů <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="1397c-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="1397c-121">Instrukce pro zpracování sděluje informace aplikaci, která zpracovává XML.</span><span class="sxs-lookup"><span data-stu-id="1397c-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="1397c-122">Libovolný počet objektů <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="1397c-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="1397c-123">Komentáře budou na stejné úrovni jako kořenový element.</span><span class="sxs-lookup"><span data-stu-id="1397c-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="1397c-124">Objekt <xref:System.Xml.Linq.XComment> nemůže být prvním argumentem v seznamu, protože není platný pro dokument XML, který by měl začít s komentářem.</span><span class="sxs-lookup"><span data-stu-id="1397c-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="1397c-125">Jedna <xref:System.Xml.Linq.XDocumentType> pro DTD.</span><span class="sxs-lookup"><span data-stu-id="1397c-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="1397c-126">Při serializaci <xref:System.Xml.Linq.XDocument>, a to i v případě, že `XDocument.Declaration` je `null`, výstup bude obsahovat deklarace XML, pokud má zapisovač `Writer.Settings.OmitXmlDeclaration` nastaven na `false` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1397c-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="1397c-127">Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví verzi na "1,0" a nastaví kódování na UTF-8.</span><span class="sxs-lookup"><span data-stu-id="1397c-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="1397c-128">Použití XElement bez XDocument</span><span class="sxs-lookup"><span data-stu-id="1397c-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="1397c-129">Jak už jsme uvedli, třída <xref:System.Xml.Linq.XElement> je hlavní třídou v programovacím rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1397c-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="1397c-130">V mnoha případech aplikace nebude vyžadovat vytvoření dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1397c-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="1397c-131">Pomocí třídy <xref:System.Xml.Linq.XElement> lze vytvořit strom XML, přidat do něj další stromy XML, upravit strom XML a uložit jej.</span><span class="sxs-lookup"><span data-stu-id="1397c-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="1397c-132">Použití XDocument</span><span class="sxs-lookup"><span data-stu-id="1397c-132">Using XDocument</span></span>  
 <span data-ttu-id="1397c-133">Chcete-li vytvořit <xref:System.Xml.Linq.XDocument>, použijte funkční konstrukci stejným způsobem jako při vytváření objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1397c-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="1397c-134">Následující kód vytvoří objekt <xref:System.Xml.Linq.XDocument> a jeho přidružené objekty v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="1397c-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="1397c-135">Při kontrole souboru Test. XML získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1397c-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1397c-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1397c-136">See also</span></span>

- [<span data-ttu-id="1397c-137">Přehled programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1397c-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
