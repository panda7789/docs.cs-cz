---
title: Ukázka rozšíření volného typu
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 6cfdef1d083a25999f62c23667c9c6ea00326dca
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989795"
---
# <a name="loosely-typed-extensions-sample"></a>Ukázka rozšíření volného typu
Model Syndikačních objektů poskytuje bohatou podporu pro práci s daty rozšíření – informace, které jsou přítomny v reprezentaci XML informačního kanálu syndikace, ale nejsou <xref:System.ServiceModel.Syndication.SyndicationFeed> explicitně <xref:System.ServiceModel.Syndication.SyndicationItem>vystaveny třídami, jako jsou a. Tato ukázka znázorňuje základní techniky pro práci s daty rozšíření.  
  
 Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely tohoto příkladu. Vzory znázorněné v této ukázce však lze použít se všemi třídami syndikace, které podporují data rozšíření:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Ukázkový kód XML  
 Pro referenci se v této ukázce používá následující dokument XML.  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 Tento dokument obsahuje následující části dat rozšíření:  
  
- `myAttribute` Atribut`<feed>` elementu.  
  
- `<simpleString>`objekt.  
  
- `<DataContractExtension>`objekt.  
  
- `<XmlSerializerExtension>`objekt.  
  
- `<xElementExtension>`objekt.  
  
## <a name="writing-extension-data"></a>Zápis dat rozšíření  
 Rozšíření atributů jsou vytvořena přidáním záznamů do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Rozšíření prvků jsou vytvořena přidáním položek do <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekce. Tato rozšíření mohou základní hodnoty, jako jsou řetězce, serializace XML .NET Framework objektů nebo uzly XML kódované ručně.  
  
 Následující vzorový kód vytvoří element rozšíření s názvem `simpleString`.  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Obor názvů XML pro tento element je prázdný obor názvů ("") a jeho hodnota je textový uzel, který obsahuje řetězec "Hello, World!".  
  
 Jedním ze způsobů, jak vytvořit složitá rozšíření prvků, která se skládají z mnoha vnořených elementů, je použití rozhraní <xref:System.Runtime.Serialization.DataContractSerializer> API .NET Framework <xref:System.Xml.Serialization.XmlSerializer> pro serializaci (a i podporuje), jak je znázorněno v následujících příkladech.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 V tomto příkladu `DataContractExtension` `XmlSerializerExtension` jsou vlastní typy vytvořené pro použití s serializátorem.  
  
 Třídu lze také použít k vytvoření rozšíření prvků <xref:System.Xml.XmlReader> z instance. <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> To umožňuje snadnou integraci s rozhraními API <xref:System.Xml.Linq.XElement> pro zpracování XML, například jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Čtení dat rozšíření  
 Hodnoty pro přípony atributů lze získat vyhledáním atributu v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekci <xref:System.Xml.XmlQualifiedName> , jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Rozšíření prvků jsou k dispozici `ReadElementExtensions<T>` pomocí metody.  
  
```csharp  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 Je také možné získat `XmlReader` v jednotlivých prvcích rozšíření <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> pomocí metody.  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření silného typu](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
