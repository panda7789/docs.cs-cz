---
title: Ukázka rozšíření silného typu
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: e8c3bf202a1fb76d383f0a3fe15084d19a1d51fb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600877"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="a8dec-102">Ukázka rozšíření silného typu</span><span class="sxs-lookup"><span data-stu-id="a8dec-102">Strongly typed extensions sample</span></span>

<span data-ttu-id="a8dec-103">Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="a8dec-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="a8dec-104">Vzory znázorněné v této ukázce však lze použít se všemi třídami syndikace, které podporují data rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a8dec-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="a8dec-105">Model objektu syndikace ( <xref:System.ServiceModel.Syndication.SyndicationFeed> , <xref:System.ServiceModel.Syndication.SyndicationItem> a související třídy) podporuje volně typovaného přístupu k datům rozšíření pomocí <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> vlastností a.</span><span class="sxs-lookup"><span data-stu-id="a8dec-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="a8dec-106">Tento příklad ukazuje, jak poskytnout přístup silného typu k datům rozšíření implementací vlastních odvozených tříd <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> , které zpřístupňují určitá rozšíření specifická pro aplikaci jako vlastnosti silného typu.</span><span class="sxs-lookup"><span data-stu-id="a8dec-106">This sample shows how to provide strongly typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly typed properties.</span></span>  
  
 <span data-ttu-id="a8dec-107">Příklad ukazuje tento příklad, jak implementovat rozšiřující element definovaný v navrhovaných rozšířeních vláken Atoming pro vlákna RFC.</span><span class="sxs-lookup"><span data-stu-id="a8dec-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="a8dec-108">Toto je jenom pro demonstrační účely a tato ukázka není zamýšlená jako úplná implementace navržené specifikace.</span><span class="sxs-lookup"><span data-stu-id="a8dec-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="a8dec-109">Ukázkový kód XML</span><span class="sxs-lookup"><span data-stu-id="a8dec-109">Sample XML</span></span>  
 <span data-ttu-id="a8dec-110">Následující příklad XML ukazuje položku Atom 1,0 s přídavným `<in-reply-to>` prvkem rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a8dec-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"
                 p3:href="http://www.example.org/entries/1"
                 p3:type="application/xhtml+xml"
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="a8dec-111">`<in-reply-to>`Element určuje tři požadované atributy ( `ref` `type` a), `href` přičemž zároveň umožňuje přítomnost dalších atributů rozšíření a elementů rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a8dec-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="a8dec-112">Modelování elementu in-reply-to</span><span class="sxs-lookup"><span data-stu-id="a8dec-112">Modeling the In-Reply-To element</span></span>  
 <span data-ttu-id="a8dec-113">V této ukázce `<in-reply-to>` je prvek modelován jako CLR, který implementuje <xref:System.Xml.Serialization.IXmlSerializable> , což umožňuje jeho použití s <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="a8dec-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="a8dec-114">Také implementuje některé metody a vlastnosti pro přístup k datům elementu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="a8dec-114">It also implements some methods and properties for accessing the element's data, as shown in the following sample code.</span></span>  
  
```csharp  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="a8dec-115">`InReplyToElement`Třída implementuje vlastnosti pro požadovaný atribut (, a `HRef` `MediaType` `Source` ) a také kolekce, které mají být uloženy <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> .</span><span class="sxs-lookup"><span data-stu-id="a8dec-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="a8dec-116">`InReplyToElement`Třída implementuje <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, které umožňuje přímou kontrolu nad tím, jak se instance objektů čtou a zapisují do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="a8dec-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="a8dec-117">`ReadXml`Metoda nejprve přečte hodnoty `Ref` vlastností,, a `HRef` `Source` `MediaType` z <xref:System.Xml.XmlReader> předané do.</span><span class="sxs-lookup"><span data-stu-id="a8dec-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="a8dec-118">Všechny neznámé atributy jsou uloženy v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8dec-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="a8dec-119">Po načtení všech atributů <xref:System.Xml.XmlReader.ReadStartElement> je volána pro posunutí čtenáře k dalšímu prvku.</span><span class="sxs-lookup"><span data-stu-id="a8dec-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="a8dec-120">Vzhledem k tomu, že element, který je modelem této třídy, nemá žádné požadované podřízené položky, podřízené prvky budou uloženy do vyrovnávací paměti do `XElement` instancí a uloženy v <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekci, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a8dec-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```csharp
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new
                                 XmlQualifiedName(reader.LocalName,
                                 reader.NamespaceURI),
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="a8dec-121">V nástroji `WriteXml` `InReplyToElement` Metoda nejprve zapisuje hodnoty `Ref` `HRef` vlastností,, a `Source` `MediaType` jako atributy XML (není `WriteXml` odpovědná za zápis samotného vnějšího prvku, jak je to provedeno volajícím `WriteXml` ).</span><span class="sxs-lookup"><span data-stu-id="a8dec-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="a8dec-122">Také zapisuje obsah <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> do zapisovače, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a8dec-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```csharp
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="a8dec-123">ThreadedFeed a ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="a8dec-123">ThreadedFeed and ThreadedItem</span></span>  
 <span data-ttu-id="a8dec-124">V ukázce `SyndicationItems` s `InReplyTo` rozšířeními, která jsou modelována `ThreadedItem` třídou.</span><span class="sxs-lookup"><span data-stu-id="a8dec-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="a8dec-125">Podobně `ThreadedFeed` Třída je, `SyndicationFeed` jejíž položky jsou všechny instance `ThreadedItem` .</span><span class="sxs-lookup"><span data-stu-id="a8dec-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="a8dec-126">`ThreadedFeed`Třída dědí z `SyndicationFeed` a Přepisuje `OnCreateItem` pro vrácení `ThreadedItem` .</span><span class="sxs-lookup"><span data-stu-id="a8dec-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="a8dec-127">Také implementuje metodu pro přístup do `Items` kolekce jako `ThreadedItems` , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a8dec-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="a8dec-128">Třída `ThreadedItem` dědí z `SyndicationItem` a vytváří `InReplyToElement` jako vlastnost silného typu.</span><span class="sxs-lookup"><span data-stu-id="a8dec-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly typed property.</span></span> <span data-ttu-id="a8dec-129">To zajišťuje pohodlný programový přístup k `InReplyTo` datům rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a8dec-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="a8dec-130">Také implementuje `TryParseElement` a `WriteElementExtensions` pro čtení a zápis jeho dat rozšíření, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a8dec-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,
                                                 string version)  
    {  
        if (this.InReplyTo != null &&
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8dec-131">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a8dec-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a8dec-132">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8dec-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a8dec-133">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8dec-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a8dec-134">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8dec-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8dec-135">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="a8dec-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a8dec-136">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a8dec-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a8dec-137">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="a8dec-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8dec-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a8dec-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
