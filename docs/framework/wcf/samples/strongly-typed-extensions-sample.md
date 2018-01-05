---
title: "Ukázky rozšíření silného typování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9928b6a63f30e111d0e84ae6d83b730ae15eedce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongly-typed-extensions-sample"></a>Ukázky rozšíření silného typování
Ukázce se používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely tohoto příkladu. Vzory předvedená v této ukázce lze však použít se všemi syndikace třídy, které podporují rozšíření data.  
  
 Modelu objektu syndikace (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, a související třídy) podporuje volného typu přístup k datům rozšíření pomocí <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> vlastnosti. Tento příklad ukazuje, jak poskytnout silného typu přístup k datům rozšíření implementací vlastní třídy odvozené z <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> , zpřístupnit určité rozšíření pro konkrétní aplikace jako vlastnosti silného typu.  
  
 Jako příklad tento příklad ukazuje implementaci rozšíření element definovaný v RFC rozšíření dělení na vlákna navrhované Atom. Toto je pouze pro demonstrační účely a tato ukázka neměla být úplnou implementaci navrhované specifikace.  
  
## <a name="sample-xml"></a>Ukázka kódu XML  
 Následující příklad XML ukazuje položku Atom 1.0 s další `<in-reply-to>` elementu rozšíření.  
  
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
  
 `<in-reply-to>` Element určuje tři povinné atributy (`ref`, `type` a `href`) a povolit přítomnost další rozšíření atributy a elementy rozšíření.  
  
## <a name="modeling-the-in-reply-to-element"></a>Element In-odpověď pro modelování  
 V této ukázce `<in-reply-to>` element je modelovaná jako CLR, který implementuje <xref:System.Xml.Serialization.IXmlSerializable>, což umožňuje jeho použití s <xref:System.Runtime.Serialization.DataContractSerializer>. Také implementuje některé metody a vlastnosti pro přístup k datům elementu, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 `InReplyToElement` Třída implementuje vlastnosti pro požadovaný atribut (`HRef`, `MediaType`, a `Source`) a také kolekcí, aby udržení <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.  
  
 `InReplyToElement` Třída implementuje <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, což umožňuje přímou kontrolu nad jak jsou instance objektů číst a zapisovat do souboru XML. `ReadXml` Metoda nejprve načte hodnoty `Ref`, `HRef`, `Source`, a `MediaType` vlastnosti z <xref:System.Xml.XmlReader> do ní předán. Všechny neznámé atributy jsou uložené v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce. Pokud byly načteny všechny atributy, <xref:System.Xml.XmlReader.ReadStartElement> nazývá posunut čtečky na další prvek. Vzhledem k tomu, že element modelovány pomocí Tato třída nemá žádné podřízené objekty požadované, získat podřízených elementů do vyrovnávací paměti do `XElement` instance a uloženy v <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekce, jak je znázorněno v následujícím kódu.  
  
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
  
 V `WriteXml`, `InReplyToElement` metoda nejprve zapíše na hodnoty `Ref`, `HRef`, `Source`, a `MediaType` vlastnosti jako atributy XML (`WriteXml` není zodpovědná za zápisu skutečné vnějšího elementu vlastní, který provádí volající `WriteXml`). Také zapíše obsah <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> a <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> Writer, jak je znázorněno v následujícím kódu.  
  
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
 V ukázce `SyndicationItems` s `InReplyTo` rozšíření jsou modelovány pomocí `ThreadedItem` třídy. Podobně `ThreadedFeed` třída je `SyndicationFeed` jehož položky jsou všechny instance `ThreadedItem`.  
  
 `ThreadedFeed` Třída dědí z `SyndicationFeed` a přepíše `OnCreateItem` vrátit `ThreadedItem`. Také implementuje metodu pro přístup k `Items` kolekci jako `ThreadedItems`, jak je znázorněno v následujícím kódu.  
  
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
  
 Třída `ThreadedItem` dědí z `SyndicationItem` díky `InReplyToElement` jako vlastnost silného typu. To umožňuje pohodlný programový přístup ke `InReplyTo` rozšíření dat. Také implementuje `TryParseElement` a `WriteElementExtensions` pro čtení a zápis svá data rozšíření, jak je znázorněno v následujícím kódu.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
  
## <a name="see-also"></a>Viz také
