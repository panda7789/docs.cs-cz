---
title: Ukázka rozšíření volného typu
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 4d92f45382361c61fe9e7ac85ff5d604a2c87b27
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592204"
---
# <a name="loosely-typed-extensions-sample"></a>Ukázka rozšíření volného typu
Poskytuje objektového modelu syndikace Rozsáhlá podpora pro práci s daty rozšíření – informace, které jsou k dispozici v informačního kanálu syndikace je reprezentovaný pomocí XML, ale vystavené třídy nejsou explicitně jako <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem>. Tento příklad ukazuje základní postupy pro práci s daty rozšíření.  
  
 Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídy pro účely tohoto příkladu. Tyto vzory se dají v této ukázce jsme vám ukázali lze však použít se všemi syndikace třídy, které podporují rozšíření dat:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Ukázkový soubor XML  
 Pro srovnání následujícího dokumentu XML se používá v této ukázce.  
  
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
  
 Tento dokument obsahuje následující časti dat rozšíření:  
  
- `myAttribute` Atribut `<feed>` elementu.  
  
- `<simpleString>` element.  
  
- `<DataContractExtension>` element.  
  
- `<XmlSerializerExtension>` element.  
  
- `<xElementExtension>` element.  
  
## <a name="writing-extension-data"></a>Zápis dat rozšíření  
 Atribut rozšíření jsou vytvořena přidáním položky <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Element rozšíření jsou vytvořena přidáním položky <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekce. Tato rozšíření lze základních hodnot, jako je například řetězce, XML serializations objekty rozhraní .NET Framework, nebo z uzlů XML zakódované ručně.  
  
 Následující ukázkový kód vytvoří rozšíření element s názvem `simpleString`.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Obor názvů XML pro tento element je prázdný obor názvů ("") a její hodnota je textový uzel, který obsahuje řetězec "hello, world!".  
  
 Jeden ze způsobů, jak vytvořit rozšíření komplexních prvků, které se skládají z mnoha je vnořené elementy k použití rozhraní API .NET Framework pro serializaci (jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány) jak je znázorněno v následujícím příkladu.  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 V tomto příkladu `DataContractExtension` a `XmlSerializerExtension` vlastní typy, které jsou napsané pro použití s serializátor.  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Třídy lze také vytvořit element rozšíření ze <xref:System.Xml.XmlReader> instance. To umožňuje snadnou integraci s XML zpracování rozhraní API, jako <xref:System.Xml.Linq.XElement> jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Čtení dat rozšíření  
 Hodnoty pro atribut rozšíření můžete získat výčtem vyhledávání atributů v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekci podle jeho <xref:System.Xml.XmlQualifiedName> jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Element rozšíření jsou přístupné pomocí `ReadElementExtensions<T>` metody.  
  
```  
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
  
 Je také možné získat `XmlReader` na jednotlivý element rozšíření pomocí <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> metody.  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření silného typu](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
