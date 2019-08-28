---
title: Ukázky rozšíření silného typování
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 1fd873e02dcc1fc824c8b17c52231c80c61e7c60
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045488"
---
# <a name="strongly-typed-extensions-sample"></a>Ukázky rozšíření silného typování
Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely tohoto příkladu. Vzory znázorněné v této ukázce však lze použít se všemi třídami syndikace, které podporují data rozšíření.  
  
 Model objektu syndikace (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>a související třídy) podporuje volně typovaného přístupu k datům <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> rozšíření pomocí vlastností a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> . Tento příklad ukazuje, jak poskytnout silně typovaného přístupu k datům rozšíření implementací vlastních odvozených tříd <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> , které zpřístupňují určitá rozšíření specifická pro aplikaci jako vlastnosti silného typu.  
  
 Příklad ukazuje tento příklad, jak implementovat rozšiřující element definovaný v navrhovaných rozšířeních vláken Atoming pro vlákna RFC. Toto je jenom pro demonstrační účely a tato ukázka není zamýšlená jako úplná implementace navržené specifikace.  
  
## <a name="sample-xml"></a>Ukázkový kód XML  
 Následující příklad XML ukazuje položku Atom 1,0 s přídavným `<in-reply-to>` prvkem rozšíření.  
  
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
  
 Element určuje tři požadované `type` atributy (`ref`a `href`), přičemž zároveň umožňuje přítomnost dalších atributů rozšíření a elementů rozšíření. `<in-reply-to>`  
  
## <a name="modeling-the-in-reply-to-element"></a>Modelování elementu in-reply-to  
 V této ukázce `<in-reply-to>` je prvek modelován jako CLR, který implementuje <xref:System.Xml.Serialization.IXmlSerializable>, což <xref:System.Runtime.Serialization.DataContractSerializer>umožňuje jeho použití s. Také implementuje některé metody a vlastnosti pro přístup k datům elementu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> `Source``HRef` `MediaType`Třída implementuje vlastnosti pro požadovaný atribut (, a) a také kolekce, které mají být uloženy a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>. `InReplyToElement`  
  
 `InReplyToElement` Třída<xref:System.Xml.Serialization.IXmlSerializable> implementuje rozhraní, které umožňuje přímou kontrolu nad tím, jak se instance objektů čtou a zapisují do formátu XML. `Source` `HRef` `Ref`Metoda nejprve přečte hodnoty vlastností`MediaType` ,, a z<xref:System.Xml.XmlReader>předanédo. `ReadXml` Všechny neznámé atributy jsou uloženy v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekci. Po načtení <xref:System.Xml.XmlReader.ReadStartElement> všech atributů je volána pro posunutí čtenáře k dalšímu prvku. Vzhledem k tomu, že element, který je modelem této třídy, nemá žádné požadované podřízené položky, `XElement` podřízené prvky budou uloženy do <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> vyrovnávací paměti do instancí a uloženy v kolekci, jak je znázorněno v následujícím kódu.  
  
```  
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
  
 `WriteXml` `Ref` `HRef` `Source`V nástroji`WriteXml` metoda nejprve zapisuje hodnoty vlastností`MediaType` ,, a jako atributy XML (není odpovědná za zápis skutečného vnějšího prvku. `InReplyToElement` sám sebe, jako to, jak to dělá `WriteXml`volající z). Také zapisuje obsah <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> do zapisovače, jak je znázorněno v následujícím kódu.  
  
```  
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
 V ukázce s `SyndicationItems` `InReplyTo` rozšířeními, která `ThreadedItem` jsou modelována třídou. Podobně `ThreadedFeed` třída `ThreadedItem`je, jejíž položky jsou všechny instance. `SyndicationFeed`  
  
 Třída dědí z `SyndicationFeed` `OnCreateItem`aPřepisuje pro vrácení. `ThreadedItem` `ThreadedFeed` Také implementuje metodu pro přístup do `Items` kolekce jako `ThreadedItems`, jak je znázorněno v následujícím kódu.  
  
```  
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
  
 Třída `ThreadedItem` dědí z `SyndicationItem` a vytváří `InReplyToElement` jako vlastnost silného typu. To zajišťuje pohodlný programový přístup k `InReplyTo` datům rozšíření. Také implementuje `TryParseElement` a `WriteElementExtensions` pro čtení a zápis jeho dat rozšíření, jak je znázorněno v následujícím kódu.  
  
```  
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
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
