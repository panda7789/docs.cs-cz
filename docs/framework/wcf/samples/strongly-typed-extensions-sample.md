---
title: Ukázky rozšíření silného typování
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 3cfbcddfdc7700618d499dd41d3a8c3b629bf550
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183306"
---
# <a name="strongly-typed-extensions-sample"></a>Ukázky rozšíření silného typování
Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely příkladu. Vzorky demonstrované v této ukázce však lze použít se všemi syndication třídy, které podporují data rozšíření.  
  
 Objektový model<xref:System.ServiceModel.Syndication.SyndicationFeed>Syndication <xref:System.ServiceModel.Syndication.SyndicationItem>( , , a související třídy) podporuje volně <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> zadaný přístup k datům rozšíření pomocí vlastností a. Tato ukázka ukazuje, jak poskytnout přístup silného typu k datům <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> rozšíření implementací vlastní odvozené třídy a které zpřístupňují některé rozšíření specifické pro aplikaci jako vlastnosti silného typu.  
  
 Jako příklad ukazuje, jak implementovat prvek rozšíření definované v navrhované rozšíření Atom threading rozšíření RFC. Toto je pouze pro demonstrační účely a tento vzorek nemá být úplným provedením navrhované specifikace.  
  
## <a name="sample-xml"></a>Ukázkový kód XML  
 Následující příklad XML ukazuje položku Atom 1.0 s dalším `<in-reply-to>` prvkem rozšíření.  
  
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
  
 Prvek `<in-reply-to>` určuje tři požadované atributy `type` `href`(`ref`, a ) a zároveň umožňuje přítomnost další chod atributy a rozšiřující prvky.  
  
## <a name="modeling-the-in-reply-to-element"></a>Modelování prvku In-Reply-To  
 V této ukázce je `<in-reply-to>` prvek modelován jako CLR, který implementuje <xref:System.Xml.Serialization.IXmlSerializable>, což umožňuje jeho použití s . <xref:System.Runtime.Serialization.DataContractSerializer> Také implementuje některé metody a vlastnosti pro přístup k datům prvku, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Třída `InReplyToElement` implementuje vlastnosti pro`HRef` `MediaType`požadovaný `Source`atribut ( , , <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>) stejně jako kolekce pro uložení a .  
  
 Třída `InReplyToElement` implementuje <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, které umožňuje přímou kontrolu nad tím, jak jsou instance objektu čteny a zapisovány do XML. Metoda `ReadXml` nejprve přečte `Ref`hodnoty `HRef` `Source`pro `MediaType` , , <xref:System.Xml.XmlReader> a vlastnosti z předány do ní. Všechny neznámé atributy jsou <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> uloženy v kolekci. Po přečtení všech atributů <xref:System.Xml.XmlReader.ReadStartElement> je volána k posunu čtenáře na další prvek. Vzhledem k tomu, že prvek modelovaný touto třídou `XElement` nemá žádné požadované <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> podřízené podřízené podřízené prvky, podřízené prvky dostanou do vyrovnávací paměti do instancí a uloží se do kolekce, jak je znázorněno v následujícím kódu.  
  
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
  
 V `WriteXml`aplikace `InReplyToElement` metoda nejprve zapíše `Ref` `HRef`hodnoty `Source`, `MediaType` , a vlastnosti jako atributy XML (`WriteXml` není zodpovědná za zápis `WriteXml`samotného skutečného vnějšího prvku, jako je tomu provedeno volajícím ). Také zapisuje <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> obsah a do zapisovače, jak je znázorněno v následujícím kódu.  
  
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
  
## <a name="threadedfeed-and-threadeditem"></a>ThreadedFeed a ThreadedItem  
 V ukázce `SyndicationItems` s `InReplyTo` rozšířeníjsou `ThreadedItem` modelovány podle třídy. Podobně `ThreadedFeed` třída `SyndicationFeed` je, jejichž položky jsou `ThreadedItem`všechny instance .  
  
 Třída `ThreadedFeed` dědí `SyndicationFeed` z a `OnCreateItem` přepíše `ThreadedItem`vrátit . Také implementuje metodu pro `Items` přístup `ThreadedItems`ke kolekci jako , jak je znázorněno v následujícím kódu.  
  
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
  
 Třída `ThreadedItem` dědí `SyndicationItem` z `InReplyToElement` a provádí jako vlastnost silného typu. To poskytuje pohodlný programový `InReplyTo` přístup k datům rozšíření. Také `TryParseElement` implementuje `WriteElementExtensions` a pro čtení a zápis dat rozšíření, jak je znázorněno v následujícím kódu.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
