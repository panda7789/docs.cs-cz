---
title: Ukládání a zápis dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 0af160b720b9eddd9e72689c920316bffdc6d21e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710216"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="34ae4-102">Ukládání a zápis dokumentu</span><span class="sxs-lookup"><span data-stu-id="34ae4-102">Saving and Writing a Document</span></span>
<span data-ttu-id="34ae4-103">Když načtete a uložíte <xref:System.Xml.XmlDocument>, uložený dokument se může lišit od originálu následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="34ae4-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="34ae4-104">Pokud je vlastnost <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> nastavena na `true` před voláním metody <xref:System.Xml.XmlDocument.Save%2A>, prázdné místo v dokumentu zůstane ve výstupu. Pokud je tato vlastnost `false`, <xref:System.Xml.XmlDocument> automaticky odsadí výstup.</span><span class="sxs-lookup"><span data-stu-id="34ae4-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="34ae4-105">Všechny prázdné znaky mezi atributy jsou zmenšeny na jeden znak mezery.</span><span class="sxs-lookup"><span data-stu-id="34ae4-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="34ae4-106">Je změněno prázdné místo mezi prvky.</span><span class="sxs-lookup"><span data-stu-id="34ae4-106">The white space between elements is changed.</span></span> <span data-ttu-id="34ae4-107">Významné prázdné znaky jsou zachovány a nevýznamné prázdné znaky nejsou.</span><span class="sxs-lookup"><span data-stu-id="34ae4-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="34ae4-108">Ale když se dokument uloží, použije se ve výchozím nastavení <xref:System.Xml.XmlTextWriter> režim **odsazení** , aby se výstup vytiskl, takže se bude čitelnější.</span><span class="sxs-lookup"><span data-stu-id="34ae4-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="34ae4-109">Znak citace použitý kolem hodnot atributů se ve výchozím nastavení změní na dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="34ae4-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="34ae4-110">Vlastnost <xref:System.Xml.XmlTextReader.QuoteChar%2A> v <xref:System.Xml.XmlTextWriter> můžete použít k nastavení znaku uvozovky na dvojité uvozovky nebo jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="34ae4-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="34ae4-111">Ve výchozím nastavení jsou rozbalené číselné znakové entity, jako je `{`.</span><span class="sxs-lookup"><span data-stu-id="34ae4-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="34ae4-112">Značka pořadí bajtů, která se nachází ve vstupním dokumentu, se nezachová.</span><span class="sxs-lookup"><span data-stu-id="34ae4-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="34ae4-113">UCS-2 je uložen jako UTF-8, pokud explicitně nevytvoříte deklaraci XML, která určuje jiné kódování.</span><span class="sxs-lookup"><span data-stu-id="34ae4-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="34ae4-114">Pokud chcete <xref:System.Xml.XmlDocument> zapsat do souboru nebo datového proudu, vypsaný výstup je stejný jako obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="34ae4-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="34ae4-115">To znamená, že <xref:System.Xml.XmlDeclaration> je zapsána pouze v případě, že je obsažena v dokumentu a kódování použité při vypisování dokumentu je stejné kódování, které je zadáno v uzlu deklarace.</span><span class="sxs-lookup"><span data-stu-id="34ae4-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="34ae4-116">Zápis XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="34ae4-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="34ae4-117"><xref:System.Xml.XmlDocument> a <xref:System.Xml.XmlDeclaration> členové <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>a <xref:System.Xml.XmlNode.WriteTo%2A>, kromě <xref:System.Xml.XmlDocument>ch metod <xref:System.Xml.XmlDocument.Save%2A> a <xref:System.Xml.XmlDocument.WriteContentTo%2A>, vytvoří deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="34ae4-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="34ae4-118">Pro <xref:System.Xml.XmlDocument> vlastností <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>a metod <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>a <xref:System.Xml.XmlDocument.WriteContentTo%2A> se kódování zapsané v deklaraci XML povede z uzlu <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="34ae4-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="34ae4-119">Pokud uzel není <xref:System.Xml.XmlDeclaration>, <xref:System.Xml.XmlDeclaration> nebude zapsán. Pokud není v uzlu <xref:System.Xml.XmlDeclaration> žádné kódování, kódování není zapsáno v deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="34ae4-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="34ae4-120">Metody <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> a <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> vždy vypisují <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="34ae4-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="34ae4-121">Tyto metody přebírají kódování od zapisovače, do kterého se zapisuje.</span><span class="sxs-lookup"><span data-stu-id="34ae4-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="34ae4-122">To znamená, že hodnota kódování u zapisovače Přepisuje kódování v dokumentu a <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="34ae4-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="34ae4-123">Například následující kód nepíše kódování v deklaraci XML, které se nachází ve výstupním souboru `out.xml`.</span><span class="sxs-lookup"><span data-stu-id="34ae4-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
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
  
 <span data-ttu-id="34ae4-124">Pro metodu <xref:System.Xml.XmlDocument.Save%2A> se deklarace XML zapisuje pomocí metody <xref:System.Xml.XmlWriter.WriteStartDocument%2A> ve třídě <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="34ae4-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="34ae4-125">Proto přepsání metody <xref:System.Xml.XmlWriter.WriteStartDocument%2A> mění způsob, jakým je zapsán začátek dokumentu.</span><span class="sxs-lookup"><span data-stu-id="34ae4-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="34ae4-126">V případě <xref:System.Xml.XmlDeclaration>ch členů <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>a <xref:System.Xml.XmlNode.InnerXml%2A>, pokud vlastnost <xref:System.Xml.XmlDeclaration.Encoding%2A> není nastavena, nezapisuje se žádné kódování. Jinak kódování zapsané v deklaraci XML je stejné jako kódování nalezené ve vlastnosti <xref:System.Xml.XmlDeclaration.Encoding%2A>.</span><span class="sxs-lookup"><span data-stu-id="34ae4-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="34ae4-127">Zápis obsahu dokumentu pomocí vlastnosti OuterXml</span><span class="sxs-lookup"><span data-stu-id="34ae4-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="34ae4-128">Vlastnost <xref:System.Xml.XmlNode.OuterXml%2A> je rozšířením Microsoft pro standardy XML model DOM (Document Object Model) (DOM) konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="34ae4-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="34ae4-129">Vlastnost <xref:System.Xml.XmlNode.OuterXml%2A> slouží k získání značky celého dokumentu XML, nebo pouze označení jednoho uzlu a jeho podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="34ae4-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="34ae4-130"><xref:System.Xml.XmlNode.OuterXml%2A> vrátí značku reprezentující daný uzel a všechny jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="34ae4-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="34ae4-131">Následující ukázka kódu ukazuje, jak uložit dokument jako celek jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="34ae4-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
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
  
 <span data-ttu-id="34ae4-132">Následující ukázka kódu ukazuje, jak uložit pouze element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="34ae4-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="34ae4-133">Naopak můžete použít vlastnost <xref:System.Xml.XmlNode.InnerText%2A>, pokud chcete obsah podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="34ae4-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ae4-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34ae4-134">See also</span></span>

- [<span data-ttu-id="34ae4-135">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="34ae4-135">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
