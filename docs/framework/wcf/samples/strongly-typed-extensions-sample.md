---
title: Ukázky rozšíření silného typování
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 8dc6bca87989b1ee8e1ee440b0d64e2c196cc28f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978242"
---
# <a name="strongly-typed-extensions-sample"></a>Ukázky rozšíření silného typování
Ukázka používá třídu <xref:System.ServiceModel.Syndication.SyndicationFeed> pro účely tohoto příkladu. Vzory znázorněné v této ukázce však lze použít se všemi třídami syndikace, které podporují data rozšíření.  
  
 Model objektu syndikace (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>a související třídy) podporuje volně typovaného přístupu k datům rozšíření pomocí vlastností <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>. Tento příklad ukazuje, jak poskytnout silně typovaného přístupu k datům rozšíření implementací vlastních odvozených tříd <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem>, které zpřístupňují určitá rozšíření specifická pro aplikaci jako vlastnosti silného typu.  
  
 Příklad ukazuje tento příklad, jak implementovat rozšiřující element definovaný v navrhovaných rozšířeních vláken Atoming pro vlákna RFC. Toto je jenom pro demonstrační účely a tato ukázka není zamýšlená jako úplná implementace navržené specifikace.  
  
## <a name="sample-xml"></a>Ukázkový kód XML  
 Následující příklad XML ukazuje položku Atom 1,0 s dalším prvkem rozšíření `<in-reply-to>`.  
  
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
  
 Element `<in-reply-to>` určuje tři požadované atributy (`ref`, `type` a `href`) a zároveň umožňuje přítomnost dalších atributů rozšíření a elementů rozšíření.  
  
## <a name="modeling-the-in-reply-to-element"></a>Modelování elementu in-reply-to  
 V této ukázce je prvek `<in-reply-to>` modelem CLR, který implementuje <xref:System.Xml.Serialization.IXmlSerializable>, který umožňuje jeho použití s <xref:System.Runtime.Serialization.DataContractSerializer>. Také implementuje některé metody a vlastnosti pro přístup k datům elementu, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Třída `InReplyToElement` implementuje vlastnosti požadovaného atributu (`HRef`, `MediaType`a `Source`) a také kolekce, které mají být uloženy <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.  
  
 Třída `InReplyToElement` implementuje rozhraní <xref:System.Xml.Serialization.IXmlSerializable>, které umožňuje přímou kontrolu nad tím, jak se instance objektů čtou a zapisují do formátu XML. Metoda `ReadXml` nejprve přečte hodnoty vlastností `Ref`, `HRef`, `Source`a `MediaType` z <xref:System.Xml.XmlReader> předaných do ní. Všechny neznámé atributy jsou uloženy v kolekci <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>. Po načtení všech atributů je volána <xref:System.Xml.XmlReader.ReadStartElement> pro posunutí čtenáře k dalšímu prvku. Vzhledem k tomu, že element, který je modelem této třídy, nemá žádné požadované podřízené položky, podřízené prvky se uloží do vyrovnávací paměti `XElement` instancí a ukládají se do kolekce <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>, jak je znázorněno v následujícím kódu.  
  
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
  
 V `WriteXml`metoda `InReplyToElement` nejprve vypisuje hodnoty vlastností `Ref`, `HRef`, `Source`a `MediaType` jako atributy XML (`WriteXml` není odpovědná za zápis samotného vnějšího prvku. , jak to dělá volající `WriteXml`). Také zapisuje obsah <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> do zapisovače, jak je znázorněno v následujícím kódu.  
  
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
 V ukázce `SyndicationItems` s rozšířeními `InReplyTo` jsou modelovány třídou `ThreadedItem`. Podobně třída `ThreadedFeed` je `SyndicationFeed`, jejichž položky jsou všechny instance `ThreadedItem`.  
  
 Třída `ThreadedFeed` dědí z `SyndicationFeed` a Přepisuje `OnCreateItem` pro vrácení `ThreadedItem`. Implementuje také metodu pro přístup ke kolekci `Items` jako `ThreadedItems`, jak je znázorněno v následujícím kódu.  
  
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
  
 Třída `ThreadedItem` dědí z `SyndicationItem` a způsobuje `InReplyToElement` jako vlastnost silného typu. To umožňuje pohodlný programový přístup k datům rozšíření `InReplyTo`. Také implementuje `TryParseElement` a `WriteElementExtensions` pro čtení a zápis dat rozšíření, jak je znázorněno v následujícím kódu.  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
