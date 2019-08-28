---
title: Ukázka rozšíření volného typu
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 21690aebca250880a8eb51aee0821220a00bc0c0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039471"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="aa86a-102">Ukázka rozšíření volného typu</span><span class="sxs-lookup"><span data-stu-id="aa86a-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="aa86a-103">Model Syndikačních objektů poskytuje bohatou podporu pro práci s daty rozšíření – informace, které jsou přítomny v reprezentaci XML informačního kanálu syndikace, ale nejsou <xref:System.ServiceModel.Syndication.SyndicationFeed> explicitně <xref:System.ServiceModel.Syndication.SyndicationItem>vystaveny třídami, jako jsou a.</span><span class="sxs-lookup"><span data-stu-id="aa86a-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="aa86a-104">Tato ukázka znázorňuje základní techniky pro práci s daty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="aa86a-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="aa86a-105">Ukázka používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="aa86a-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="aa86a-106">Vzory znázorněné v této ukázce však lze použít se všemi třídami syndikace, které podporují data rozšíření:</span><span class="sxs-lookup"><span data-stu-id="aa86a-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="aa86a-107">Ukázkový kód XML</span><span class="sxs-lookup"><span data-stu-id="aa86a-107">Sample XML</span></span>  
 <span data-ttu-id="aa86a-108">Pro referenci se v této ukázce používá následující dokument XML.</span><span class="sxs-lookup"><span data-stu-id="aa86a-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="aa86a-109">Tento dokument obsahuje následující části dat rozšíření:</span><span class="sxs-lookup"><span data-stu-id="aa86a-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="aa86a-110">`myAttribute` Atribut`<feed>` elementu.</span><span class="sxs-lookup"><span data-stu-id="aa86a-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="aa86a-111">`<simpleString>`objekt.</span><span class="sxs-lookup"><span data-stu-id="aa86a-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="aa86a-112">`<DataContractExtension>`objekt.</span><span class="sxs-lookup"><span data-stu-id="aa86a-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="aa86a-113">`<XmlSerializerExtension>`objekt.</span><span class="sxs-lookup"><span data-stu-id="aa86a-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="aa86a-114">`<xElementExtension>`objekt.</span><span class="sxs-lookup"><span data-stu-id="aa86a-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="aa86a-115">Zápis dat rozšíření</span><span class="sxs-lookup"><span data-stu-id="aa86a-115">Writing Extension Data</span></span>  
 <span data-ttu-id="aa86a-116">Rozšíření atributů jsou vytvořena přidáním záznamů do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="aa86a-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="aa86a-117">Rozšíření prvků jsou vytvořena přidáním položek do <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="aa86a-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="aa86a-118">Tato rozšíření mohou základní hodnoty, jako jsou řetězce, serializace XML .NET Framework objektů nebo uzly XML kódované ručně.</span><span class="sxs-lookup"><span data-stu-id="aa86a-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="aa86a-119">Následující vzorový kód vytvoří element rozšíření s názvem `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="aa86a-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="aa86a-120">Obor názvů XML pro tento element je prázdný obor názvů ("") a jeho hodnota je textový uzel, který obsahuje řetězec "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="aa86a-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="aa86a-121">Jedním ze způsobů, jak vytvořit složitá rozšíření prvků, která se skládají z mnoha vnořených elementů, je použití rozhraní <xref:System.Runtime.Serialization.DataContractSerializer> API .NET Framework <xref:System.Xml.Serialization.XmlSerializer> pro serializaci (a i podporuje), jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="aa86a-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="aa86a-122">V tomto příkladu `DataContractExtension` `XmlSerializerExtension` jsou vlastní typy vytvořené pro použití s serializátorem.</span><span class="sxs-lookup"><span data-stu-id="aa86a-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="aa86a-123">Třídu lze také použít k vytvoření rozšíření prvků <xref:System.Xml.XmlReader> z instance. <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection></span><span class="sxs-lookup"><span data-stu-id="aa86a-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="aa86a-124">To umožňuje snadnou integraci s rozhraními API <xref:System.Xml.Linq.XElement> pro zpracování XML, například jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="aa86a-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="aa86a-125">Čtení dat rozšíření</span><span class="sxs-lookup"><span data-stu-id="aa86a-125">Reading Extension Data</span></span>  
 <span data-ttu-id="aa86a-126">Hodnoty pro přípony atributů lze získat vyhledáním atributu v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekci <xref:System.Xml.XmlQualifiedName> , jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="aa86a-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="aa86a-127">Rozšíření prvků jsou k dispozici `ReadElementExtensions<T>` pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="aa86a-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="aa86a-128">Je také možné získat `XmlReader` v jednotlivých prvcích rozšíření <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="aa86a-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa86a-129">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="aa86a-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="aa86a-130">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa86a-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="aa86a-131">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa86a-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="aa86a-132">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa86a-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="aa86a-133">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="aa86a-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aa86a-134">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="aa86a-134">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="aa86a-135">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="aa86a-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa86a-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="aa86a-136">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="aa86a-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa86a-137">See also</span></span>

- [<span data-ttu-id="aa86a-138">Rozšíření silného typu</span><span class="sxs-lookup"><span data-stu-id="aa86a-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="aa86a-139">Syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="aa86a-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
