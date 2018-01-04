---
title: "Ukládání a zápis dokumentu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2138b9c47c6e41cd94e775eaed005d8a6fd976c9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="19d49-102">Ukládání a zápis dokumentu</span><span class="sxs-lookup"><span data-stu-id="19d49-102">Saving and Writing a Document</span></span>
<span data-ttu-id="19d49-103">Při spouštění a uložit <xref:System.Xml.XmlDocument>, uložený dokument se můžou lišit od původního následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="19d49-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
-   <span data-ttu-id="19d49-104">Pokud <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> je nastavena na `true` před <xref:System.Xml.XmlDocument.Save%2A> metoda je volána, prázdné místo v dokumentu je zachována ve výstupu; pokud je tato vlastnost `false`, <xref:System.Xml.XmlDocument> automaticky odsazení výstup.</span><span class="sxs-lookup"><span data-stu-id="19d49-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
-   <span data-ttu-id="19d49-105">Všechny mezer mezi atributy sníží jeden mezerou.</span><span class="sxs-lookup"><span data-stu-id="19d49-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
-   <span data-ttu-id="19d49-106">Mezer mezi elementy se změní.</span><span class="sxs-lookup"><span data-stu-id="19d49-106">The white space between elements is changed.</span></span> <span data-ttu-id="19d49-107">Uchování významné prázdné znaky a není zanedbatelný prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="19d49-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="19d49-108">Při ukládání dokumentu se bude používat, ale <xref:System.Xml.XmlTextWriter> **Indenting** režimu ve výchozím nastavení přehledně vytisknout výstup, aby byl čitelnější.</span><span class="sxs-lookup"><span data-stu-id="19d49-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
-   <span data-ttu-id="19d49-109">Uvozovky používá kolem hodnoty atributu se změní na dvojitých uvozovek ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="19d49-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="19d49-110">Můžete použít <xref:System.Xml.XmlTextReader.QuoteChar%2A> vlastnost <xref:System.Xml.XmlTextWriter> nastavit uvozovky dvojité uvozovky nebo jednoduchých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="19d49-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
-   <span data-ttu-id="19d49-111">Ve výchozím nastavení, jako například entity číselné znaků `{` rozbaleny.</span><span class="sxs-lookup"><span data-stu-id="19d49-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
-   <span data-ttu-id="19d49-112">Značky pořadí bajtů nalezen v dokumentu vstupní není zachován.</span><span class="sxs-lookup"><span data-stu-id="19d49-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="19d49-113">UCS-2 je uložena jako UTF-8, pokud explicitně vytvořit deklaraci XML, který určuje jinou kódování.</span><span class="sxs-lookup"><span data-stu-id="19d49-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
-   <span data-ttu-id="19d49-114">Pokud chcete zapsat <xref:System.Xml.XmlDocument> do souboru nebo datový proud, zapsána výstup je stejný jako obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19d49-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="19d49-115">To znamená <xref:System.Xml.XmlDeclaration> je napsána pouze pokud je obsažena v dokumentu a kódování použité při zápisu se dokumentu je stejný kódování uveden v uzlu deklarace.</span><span class="sxs-lookup"><span data-stu-id="19d49-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="19d49-116">Zápis XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="19d49-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="19d49-117"><xref:System.Xml.XmlDocument> a <xref:System.Xml.XmlDeclaration> členy <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, a <xref:System.Xml.XmlNode.WriteTo%2A>, kromě <xref:System.Xml.XmlDocument> metody <xref:System.Xml.XmlDocument.Save%2A> a <xref:System.Xml.XmlDocument.WriteContentTo%2A>, vytvořit deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="19d49-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="19d49-118">Pro <xref:System.Xml.XmlDocument> vlastnosti <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>a <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, a <xref:System.Xml.XmlDocument.WriteContentTo%2A> metody, kódování napsána v deklaraci XML je převzat ze <xref:System.Xml.XmlDeclaration> uzlu.</span><span class="sxs-lookup"><span data-stu-id="19d49-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="19d49-119">Pokud neexistuje žádné <xref:System.Xml.XmlDeclaration> uzlu <xref:System.Xml.XmlDeclaration> není zapsaná. Pokud je v bez kódování <xref:System.Xml.XmlDeclaration> uzlu kódování není napsána v deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="19d49-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="19d49-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> a <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> metody vždycky zapsat <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="19d49-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="19d49-121">Tyto metody přijímají kódování z zapisovač, který zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="19d49-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="19d49-122">To znamená, kódování hodnota zapisovače přepsání kódování na dokument a na <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="19d49-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="19d49-123">Například následující kód nelze zapsat kódování v deklaraci XML nalezen ve výstupním souboru `out.xml`.</span><span class="sxs-lookup"><span data-stu-id="19d49-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="19d49-124">Pro <xref:System.Xml.XmlDocument.Save%2A> metody deklarace XML je zapsána pomocí <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda v <xref:System.Xml.XmlWriter> – třída.</span><span class="sxs-lookup"><span data-stu-id="19d49-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="19d49-125">Proto přepsal <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda mění, jak je zapsán začátek dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19d49-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="19d49-126">Pro <xref:System.Xml.XmlDeclaration> členy <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, a <xref:System.Xml.XmlNode.InnerXml%2A>, pokud <xref:System.Xml.XmlDeclaration.Encoding%2A> není nastavena vlastnost, bez kódování se zapíše. Jinak, kódování napsána v deklaraci XML je stejný jako kódování v nalezen <xref:System.Xml.XmlDeclaration.Encoding%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="19d49-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="19d49-127">Obsah dokumentu zápis pomocí vlastnosti OuterXml</span><span class="sxs-lookup"><span data-stu-id="19d49-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="19d49-128"><xref:System.Xml.XmlNode.OuterXml%2A> Vlastnost je rozšíření Microsoft standardům World Wide Web Consortium (W3C) XML modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="19d49-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="19d49-129"><xref:System.Xml.XmlNode.OuterXml%2A> Vlastnost se používá k získání kódu celý dokument XML nebo kód jeden uzel a jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="19d49-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="19d49-130"><xref:System.Xml.XmlNode.OuterXml%2A>vrátí kód, který představuje daný uzel a všechny jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="19d49-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="19d49-131">Následující příklad kódu ukazuje, jak k uložení dokumentu v celé jeho šíři jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="19d49-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="19d49-132">Následující příklad kódu ukazuje, jak uložit jenom element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19d49-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="19d49-133">Naproti tomu můžete použít <xref:System.Xml.XmlNode.InnerText%2A> vlastnost, pokud chcete, aby obsah podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="19d49-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d49-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="19d49-134">See Also</span></span>  
 [<span data-ttu-id="19d49-135">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="19d49-135">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
