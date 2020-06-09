---
title: Ukázka rozšíření volného typu
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 0a08ca19e5e6bff7223d45726617d2c2163ca3df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591862"
---
# <a name="loosely-typed-extensions-sample"></a>Ukázka rozšíření volného typu
Model Syndikačních objektů poskytuje bohatou podporu pro práci s daty rozšíření – informace, které jsou přítomny v reprezentaci XML informačního kanálu syndikace, ale nejsou explicitně vystaveny třídami, jako jsou <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> . Tato ukázka znázorňuje základní techniky pro práci s daty rozšíření.  
  
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
  
- `myAttribute`Atribut `<feed>` elementu.  
  
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
  
 Následující vzorový kód vytvoří element rozšíření s názvem `simpleString` .  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Obor názvů XML pro tento element je prázdný obor názvů ("") a jeho hodnota je textový uzel, který obsahuje řetězec "Hello, World!".  
  
 Jedním ze způsobů, jak vytvořit složitá rozšíření prvků, která se skládají z mnoha vnořených elementů, je použití rozhraní API .NET Framework pro serializaci ( <xref:System.Runtime.Serialization.DataContractSerializer> a i <xref:System.Xml.Serialization.XmlSerializer> podporuje), jak je znázorněno v následujících příkladech.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 V tomto příkladu `DataContractExtension` `XmlSerializerExtension` jsou vlastní typy vytvořené pro použití s serializátorem.  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>Třídu lze také použít k vytvoření rozšíření prvků z <xref:System.Xml.XmlReader> instance. To umožňuje snadnou integraci s rozhraními API pro zpracování XML, například <xref:System.Xml.Linq.XElement> jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Čtení dat rozšíření  
 Hodnoty pro přípony atributů lze získat vyhledáním atributu v kolekci, jak je <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.Xml.XmlQualifiedName> znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Rozšíření prvků jsou k dispozici pomocí `ReadElementExtensions<T>` metody.  
  
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
  
 Je také možné získat `XmlReader` v jednotlivých prvcích rozšíření pomocí <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> metody.  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Viz také

- [Přípony silného typu](strongly-typed-extensions-sample.md)
- [Syndikace WCF](../feature-details/wcf-syndication.md)
