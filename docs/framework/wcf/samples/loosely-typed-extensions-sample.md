---
title: Ukázka rozšíření volného typu
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: f3beed9b9ca1dd6b1d4bb32078e6cd35a636501c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714870"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="4a543-102">Ukázka rozšíření volného typu</span><span class="sxs-lookup"><span data-stu-id="4a543-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="4a543-103">Model objektu syndikace nabízí bohatou podporu pro práci s daty rozšíření – informace, které jsou přítomny v reprezentaci XML informačního kanálu syndikace, ale nejsou explicitně vystaveny třídami, jako jsou <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="4a543-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="4a543-104">Tato ukázka znázorňuje základní techniky pro práci s daty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4a543-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="4a543-105">Ukázka používá třídu <xref:System.ServiceModel.Syndication.SyndicationFeed> pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4a543-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="4a543-106">Vzory znázorněné v této ukázce však lze použít se všemi třídami syndikace, které podporují data rozšíření:</span><span class="sxs-lookup"><span data-stu-id="4a543-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="4a543-107">Ukázkový kód XML</span><span class="sxs-lookup"><span data-stu-id="4a543-107">Sample XML</span></span>  
 <span data-ttu-id="4a543-108">Pro referenci se v této ukázce používá následující dokument XML.</span><span class="sxs-lookup"><span data-stu-id="4a543-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="4a543-109">Tento dokument obsahuje následující části dat rozšíření:</span><span class="sxs-lookup"><span data-stu-id="4a543-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="4a543-110">Atribut `myAttribute` elementu `<feed>`</span><span class="sxs-lookup"><span data-stu-id="4a543-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="4a543-111">element `<simpleString>`.</span><span class="sxs-lookup"><span data-stu-id="4a543-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="4a543-112">element `<DataContractExtension>`.</span><span class="sxs-lookup"><span data-stu-id="4a543-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="4a543-113">element `<XmlSerializerExtension>`.</span><span class="sxs-lookup"><span data-stu-id="4a543-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="4a543-114">element `<xElementExtension>`.</span><span class="sxs-lookup"><span data-stu-id="4a543-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="4a543-115">Zápis dat rozšíření</span><span class="sxs-lookup"><span data-stu-id="4a543-115">Writing Extension Data</span></span>  
 <span data-ttu-id="4a543-116">Rozšíření atributů jsou vytvořena přidáním položek do kolekce <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4a543-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="4a543-117">Rozšíření prvků jsou vytvořena přidáním položek do kolekce <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a543-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="4a543-118">Tato rozšíření mohou základní hodnoty, jako jsou řetězce, serializace XML .NET Framework objektů nebo uzly XML kódované ručně.</span><span class="sxs-lookup"><span data-stu-id="4a543-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="4a543-119">Následující vzorový kód vytvoří element rozšíření s názvem `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="4a543-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="4a543-120">Obor názvů XML pro tento element je prázdný obor názvů ("") a jeho hodnota je textový uzel, který obsahuje řetězec "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="4a543-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="4a543-121">Jedním ze způsobů, jak vytvořit složitá rozšíření prvků, která se skládají z mnoha vnořených elementů, je použít rozhraní .NET Framework API pro serializaci (jsou podporovány <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer>), jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="4a543-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="4a543-122">V tomto příkladu jsou `DataContractExtension` a `XmlSerializerExtension` vlastní typy zapsané pro použití s serializátorem.</span><span class="sxs-lookup"><span data-stu-id="4a543-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="4a543-123">Třídu <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> lze také použít k vytvoření rozšíření prvku z instance <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4a543-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="4a543-124">To umožňuje snadnou integraci s rozhraními API pro zpracování XML, jako je například <xref:System.Xml.Linq.XElement>, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4a543-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="4a543-125">Čtení dat rozšíření</span><span class="sxs-lookup"><span data-stu-id="4a543-125">Reading Extension Data</span></span>  
 <span data-ttu-id="4a543-126">Hodnoty pro přípony atributů lze získat vyhledáním atributu v kolekci <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> pomocí jeho <xref:System.Xml.XmlQualifiedName>, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4a543-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="4a543-127">Rozšíření prvků jsou k dispozici pomocí metody `ReadElementExtensions<T>`.</span><span class="sxs-lookup"><span data-stu-id="4a543-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="4a543-128">Je také možné získat `XmlReader` v jednotlivých rozšířeních prvků pomocí metody <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>.</span><span class="sxs-lookup"><span data-stu-id="4a543-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4a543-129">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4a543-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4a543-130">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a543-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4a543-131">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a543-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4a543-132">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a543-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4a543-133">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="4a543-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4a543-134">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4a543-134">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4a543-135">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="4a543-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4a543-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4a543-136">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="4a543-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a543-137">See also</span></span>

- [<span data-ttu-id="4a543-138">Rozšíření silného typu</span><span class="sxs-lookup"><span data-stu-id="4a543-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="4a543-139">Syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="4a543-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
