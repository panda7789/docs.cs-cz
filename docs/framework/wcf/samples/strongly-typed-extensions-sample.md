---
title: Ukázky rozšíření silného typování
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: eeef3fd05c66031fb2be573b1c1f56a35a3301ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007783"
---
# <a name="strongly-typed-extensions-sample"></a>Ukázky rozšíření silného typování
Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídy pro účely tohoto příkladu. Tyto vzory se dají v této ukázce jsme vám ukázali lze však použít se všemi syndikace třídy, které podporují dat rozšíření.  
  
 Objektového modelu syndikace (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, a související třídy) podporuje volného typu přístup k datům rozšíření pomocí <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> vlastnosti. Tento příklad ukazuje, jak poskytovat přístup k datům rozšíření s silného typu pomocí implementace vlastní třídy odvozené z <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> , uvolněte některá rozšíření specifické pro aplikaci jako silného typu vlastnosti.  
  
 Jako příklad Tato ukázka předvádí, jak implementovat rozšíření element definovaný v RFC rozšíření dělení na vlákna navrhovaných Atom. Toto je pouze pro demonstrační účely a tento příklad nemá představovat úplnou implementaci daného navrhovaných specifikace.  
  
## <a name="sample-xml"></a>Ukázkový soubor XML  
 Následující ukázkový kód XML zobrazuje položka Atom 1.0 ještě `<in-reply-to>` element rozšíření.  
  
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
  
 `<in-reply-to>` Prvek určuje tři povinné atributy (`ref`, `type` a `href`) a zároveň přítomnost další rozšíření atributy a elementy rozšíření.  
  
## <a name="modeling-the-in-reply-to-element"></a>In – odpovědi na prvku modelu  
 V této ukázce `<in-reply-to>` element je modelovaná jako CLR, který implementuje <xref:System.Xml.Serialization.IXmlSerializable>, což umožňuje jeho použití s <xref:System.Runtime.Serialization.DataContractSerializer>. Také implementuje některé metody a vlastnosti pro přístup k datům element, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 `InReplyToElement` Třída implementuje vlastnosti pro požadovaný atribut (`HRef`, `MediaType`, a `Source`) a také kolekce pro uložení <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.  
  
 `InReplyToElement` Implementuje třída <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, což umožňuje přímou kontrolu nad jak instance objektů se čtou a zapisují do souboru XML. `ReadXml` Metoda nejprve čte hodnoty `Ref`, `HRef`, `Source`, a `MediaType` vlastnosti z <xref:System.Xml.XmlReader> do něho předaný. Všechny neznámé atributy jsou uloženy v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce. Přečtení všechny atributy <xref:System.Xml.XmlReader.ReadStartElement> je volána k přechodu čtenáře na další prvek. Vzhledem k tomu, že element modelovaná Tato třída nemá žádné požadované podřízené položky, získat podřízené prvky do vyrovnávací paměti do `XElement` instance a uložená v <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekce, jak je znázorněno v následujícím kódu.  
  
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
  
 V `WriteXml`, `InReplyToElement` metoda nejprve zapíše hodnoty `Ref`, `HRef`, `Source`, a `MediaType` vlastnosti jako atributy ve formátu XML (`WriteXml` není odpovídají za zápis skutečné vnější element samostatně jako, který provádí volající `WriteXml`). Také zapíše obsah <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> Writer, jak je znázorněno v následujícím kódu.  
  
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
 V ukázce `SyndicationItems` s `InReplyTo` rozšíření jsou modelovány pomocí `ThreadedItem` třídy. Podobně `ThreadedFeed` třída je `SyndicationFeed` jehož položky jsou všechny výskyty `ThreadedItem`.  
  
 `ThreadedFeed` Třída dědí z `SyndicationFeed` a přepíše `OnCreateItem` se vraťte `ThreadedItem`. Také implementuje metodu pro přístup k `Items` kolekci jako `ThreadedItems`, jak je znázorněno v následujícím kódu.  
  
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
  
 Třída `ThreadedItem` dědí z `SyndicationItem` a zpřístupňuje `InReplyToElement` jako vlastnost silného typu. To umožňuje pohodlný programový přístup k `InReplyTo` dat rozšíření. Implementuje navíc `TryParseElement` a `WriteElementExtensions` pro čtení a zápis dat rozšíření, jak je znázorněno v následujícím kódu.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
