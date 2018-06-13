---
title: Ukázka rozšíření volného typu
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 9ad00c1e76d14b32cb28216cfdbb1a01f82a70cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504434"
---
# <a name="loosely-typed-extensions-sample"></a>Ukázka rozšíření volného typu
Modelu objektu syndikace poskytuje bohaté podporu pro práci s daty rozšíření – informace, které se nachází v syndikace kanál reprezentovaný pomocí XML je ale vystavené třídy není explicitně jako <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem>. Tento příklad ukazuje základní postupy pro práci s daty rozšíření.  
  
 Ukázce se používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely tohoto příkladu. Vzory předvedená v této ukázce lze však použít se všemi syndikace třídy, které podporují rozšíření dat:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Ukázka kódu XML  
 Pro odkaz se v této ukázce používá následující dokument XML.  
  
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
  
 Tento dokument obsahuje následující rozšíření dat:  
  
-   `myAttribute` Atribut `<feed>` elementu.  
  
-   `<simpleString>` element.  
  
-   `<DataContractExtension>` element.  
  
-   `<XmlSerializerExtension>` element.  
  
-   `<xElementExtension>` element.  
  
## <a name="writing-extension-data"></a>Zápis dat rozšíření  
 Vytváří přidávání položek do atribut rozšíření <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Element rozšíření jsou vytvořené pomocí přidání položek <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekce. Tato rozšíření můžou základní hodnoty, jako je například řetězce, XML serializations objekty rozhraní .NET Framework, nebo z uzlů XML programového ručně.  
  
 Následující vzorový kód vytvoří rozšíření element s názvem `simpleString`.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Obor názvů XML pro tento element je prázdný obor názvů ("") a jeho hodnota je textový uzel, který obsahuje text "hello, world!".  
  
 Jeden ze způsobů, jak vytvořit komplexní element rozšíření, které se skládají z mnoha vnořených elementů je použití rozhraní API rozhraní .NET Framework pro serializaci (jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány) podle následujících příkladů.  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 V tomto příkladu `DataContractExtension` a `XmlSerializerExtension` jsou vlastní typy, které jsou napsané pro použití s označuje, že serializátor.  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Třídy lze také vytvořit element rozšíření z <xref:System.Xml.XmlReader> instance. To umožňuje snadnou integraci s XML, jako zpracování rozhraní API <xref:System.Xml.Linq.XElement> jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Čtení dat rozšíření  
 Je možné získat hodnoty pro atribut rozšíření vyhledávání atributů v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce podle jeho <xref:System.Xml.XmlQualifiedName> jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Element rozšíření ke kterým se přistupuje pomocí `ReadElementExtensions<T>` metoda.  
  
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
  
 Je také možné získat `XmlReader` v rozšíření jednotlivý prvek pomocí <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> metoda.  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření silného typu](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)  
 [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
