---
title: Ukázka rozšíření volného typu
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: b8d1d42864b8764551cc44a26d820090eb28971e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183540"
---
# <a name="loosely-typed-extensions-sample"></a>Ukázka rozšíření volného typu
Objektový model Syndication poskytuje bohatou podporu pro práci s daty rozšíření – informace, které jsou přítomny v reprezentaci XML zdroje syndikace, ale nejsou explicitně vystaveny třídám, jako <xref:System.ServiceModel.Syndication.SyndicationFeed> jsou a <xref:System.ServiceModel.Syndication.SyndicationItem>. Tato ukázka ilustruje základní techniky pro práci s daty rozšíření.  
  
 Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely příkladu. Vzorky demonstrované v této ukázce však lze použít se všemi třídami Syndication, které podporují data rozšíření:  
  
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
  
- Atribut `myAttribute` `<feed>` prvku.  
  
- `<simpleString>`Prvek.  
  
- `<DataContractExtension>`Prvek.  
  
- `<XmlSerializerExtension>`Prvek.  
  
- `<xElementExtension>`Prvek.  
  
## <a name="writing-extension-data"></a>Zápis dat rozšíření  
 Rozšíření atributů jsou vytvořena přidáním položek do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Rozšíření prvků jsou vytvořeny přidáním <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> položek do kolekce. Tato rozšíření mohou být pomocí základních hodnot, jako jsou řetězce, serializace XML objektů rozhraní .NET Framework nebo uzly XML kódované ručně.  
  
 Následující ukázkový kód vytvoří `simpleString`prvek rozšíření s názvem .  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Obor názvů XML pro tento prvek je prázdný obor názvů ("") a jeho hodnota je textový uzel, který obsahuje řetězec "hello, world!".  
  
 Jedním ze způsobů, jak vytvořit rozšíření složitých prvků, které se skládají z mnoha <xref:System.Runtime.Serialization.DataContractSerializer> vnořených prvků, je použití rozhraní API rozhraní .NET Framework pro serializaci (podporovány i <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány), jak je znázorněno v následujících příkladech.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 V tomto `DataContractExtension` příkladu `XmlSerializerExtension` a jsou vlastní typy napsané pro použití s serializátorem.  
  
 Třídu <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> lze také použít k vytvoření <xref:System.Xml.XmlReader> rozšíření elementu z instance. To umožňuje snadnou integraci s rozhraními API pro zpracování XML, například <xref:System.Xml.Linq.XElement> jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Čtení dat rozšíření  
 Hodnoty pro rozšíření atributů lze získat tak, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> že se <xref:System.Xml.XmlQualifiedName> atribut v kolekci zobrazí podle následujícího ukázkového kódu.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Rozšíření prvků jsou přístupné `ReadElementExtensions<T>` pomocí metody.  
  
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
  
 Je také možné získat `XmlReader` na jednotlivé rozšíření prvku <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> pomocí metody.  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Viz také

- [Rozšíření silného typu](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
