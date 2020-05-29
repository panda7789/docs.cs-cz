---
title: Ukázka rozšíření volného typu
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 5d3defacc4a0acee69e32667d0d9213320b3ccec
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202228"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="3a113-102">Ukázka rozšíření volného typu</span><span class="sxs-lookup"><span data-stu-id="3a113-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="3a113-103">Model Syndikačních objektů poskytuje bohatou podporu pro práci s daty rozšíření – informace, které jsou přítomny v reprezentaci XML informačního kanálu syndikace, ale nejsou explicitně vystaveny třídami, jako jsou <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> .</span><span class="sxs-lookup"><span data-stu-id="3a113-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="3a113-104">Tato ukázka znázorňuje základní techniky pro práci s daty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3a113-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="3a113-105">Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="3a113-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="3a113-106">Vzory znázorněné v této ukázce však lze použít se všemi třídami syndikace, které podporují data rozšíření:</span><span class="sxs-lookup"><span data-stu-id="3a113-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="3a113-107">Ukázkový kód XML</span><span class="sxs-lookup"><span data-stu-id="3a113-107">Sample XML</span></span>  
 <span data-ttu-id="3a113-108">Pro referenci se v této ukázce používá následující dokument XML.</span><span class="sxs-lookup"><span data-stu-id="3a113-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="3a113-109">Tento dokument obsahuje následující části dat rozšíření:</span><span class="sxs-lookup"><span data-stu-id="3a113-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="3a113-110">`myAttribute`Atribut `<feed>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3a113-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="3a113-111">`<simpleString>`objekt.</span><span class="sxs-lookup"><span data-stu-id="3a113-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="3a113-112">`<DataContractExtension>`objekt.</span><span class="sxs-lookup"><span data-stu-id="3a113-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="3a113-113">`<XmlSerializerExtension>`objekt.</span><span class="sxs-lookup"><span data-stu-id="3a113-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="3a113-114">`<xElementExtension>`objekt.</span><span class="sxs-lookup"><span data-stu-id="3a113-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="3a113-115">Zápis dat rozšíření</span><span class="sxs-lookup"><span data-stu-id="3a113-115">Writing Extension Data</span></span>  
 <span data-ttu-id="3a113-116">Rozšíření atributů jsou vytvořena přidáním záznamů do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="3a113-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="3a113-117">Rozšíření prvků jsou vytvořena přidáním položek do <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="3a113-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="3a113-118">Tato rozšíření mohou základní hodnoty, jako jsou řetězce, serializace XML .NET Framework objektů nebo uzly XML kódované ručně.</span><span class="sxs-lookup"><span data-stu-id="3a113-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="3a113-119">Následující vzorový kód vytvoří element rozšíření s názvem `simpleString` .</span><span class="sxs-lookup"><span data-stu-id="3a113-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="3a113-120">Obor názvů XML pro tento element je prázdný obor názvů ("") a jeho hodnota je textový uzel, který obsahuje řetězec "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="3a113-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="3a113-121">Jedním ze způsobů, jak vytvořit složitá rozšíření prvků, která se skládají z mnoha vnořených elementů, je použití rozhraní API .NET Framework pro serializaci ( <xref:System.Runtime.Serialization.DataContractSerializer> a i <xref:System.Xml.Serialization.XmlSerializer> podporuje), jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="3a113-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="3a113-122">V tomto příkladu `DataContractExtension` `XmlSerializerExtension` jsou vlastní typy vytvořené pro použití s serializátorem.</span><span class="sxs-lookup"><span data-stu-id="3a113-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="3a113-123"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>Třídu lze také použít k vytvoření rozšíření prvků z <xref:System.Xml.XmlReader> instance.</span><span class="sxs-lookup"><span data-stu-id="3a113-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="3a113-124">To umožňuje snadnou integraci s rozhraními API pro zpracování XML, například <xref:System.Xml.Linq.XElement> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="3a113-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="3a113-125">Čtení dat rozšíření</span><span class="sxs-lookup"><span data-stu-id="3a113-125">Reading Extension Data</span></span>  
 <span data-ttu-id="3a113-126">Hodnoty pro přípony atributů lze získat vyhledáním atributu v kolekci, jak je <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.Xml.XmlQualifiedName> znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="3a113-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="3a113-127">Rozšíření prvků jsou k dispozici pomocí `ReadElementExtensions<T>` metody.</span><span class="sxs-lookup"><span data-stu-id="3a113-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="3a113-128">Je také možné získat `XmlReader` v jednotlivých prvcích rozšíření pomocí <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> metody.</span><span class="sxs-lookup"><span data-stu-id="3a113-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a113-129">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3a113-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3a113-130">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a113-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3a113-131">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a113-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3a113-132">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a113-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a113-133">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="3a113-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a113-134">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3a113-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3a113-135">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="3a113-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a113-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3a113-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="3a113-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a113-137">See also</span></span>

- [<span data-ttu-id="3a113-138">Přípony silného typu</span><span class="sxs-lookup"><span data-stu-id="3a113-138">Strongly typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="3a113-139">Syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="3a113-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
