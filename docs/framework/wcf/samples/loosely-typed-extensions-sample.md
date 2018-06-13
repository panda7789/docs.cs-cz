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
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="c7da6-102">Ukázka rozšíření volného typu</span><span class="sxs-lookup"><span data-stu-id="c7da6-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="c7da6-103">Modelu objektu syndikace poskytuje bohaté podporu pro práci s daty rozšíření – informace, které se nachází v syndikace kanál reprezentovaný pomocí XML je ale vystavené třídy není explicitně jako <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="c7da6-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="c7da6-104">Tento příklad ukazuje základní postupy pro práci s daty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c7da6-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="c7da6-105">Ukázce se používá <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7da6-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="c7da6-106">Vzory předvedená v této ukázce lze však použít se všemi syndikace třídy, které podporují rozšíření dat:</span><span class="sxs-lookup"><span data-stu-id="c7da6-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="c7da6-107">Ukázka kódu XML</span><span class="sxs-lookup"><span data-stu-id="c7da6-107">Sample XML</span></span>  
 <span data-ttu-id="c7da6-108">Pro odkaz se v této ukázce používá následující dokument XML.</span><span class="sxs-lookup"><span data-stu-id="c7da6-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="c7da6-109">Tento dokument obsahuje následující rozšíření dat:</span><span class="sxs-lookup"><span data-stu-id="c7da6-109">This document contains the following pieces of extension data:</span></span>  
  
-   <span data-ttu-id="c7da6-110">`myAttribute` Atribut `<feed>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c7da6-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
-   <span data-ttu-id="c7da6-111">`<simpleString>` element.</span><span class="sxs-lookup"><span data-stu-id="c7da6-111">`<simpleString>` element.</span></span>  
  
-   <span data-ttu-id="c7da6-112">`<DataContractExtension>` element.</span><span class="sxs-lookup"><span data-stu-id="c7da6-112">`<DataContractExtension>` element.</span></span>  
  
-   <span data-ttu-id="c7da6-113">`<XmlSerializerExtension>` element.</span><span class="sxs-lookup"><span data-stu-id="c7da6-113">`<XmlSerializerExtension>` element.</span></span>  
  
-   <span data-ttu-id="c7da6-114">`<xElementExtension>` element.</span><span class="sxs-lookup"><span data-stu-id="c7da6-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="c7da6-115">Zápis dat rozšíření</span><span class="sxs-lookup"><span data-stu-id="c7da6-115">Writing Extension Data</span></span>  
 <span data-ttu-id="c7da6-116">Vytváří přidávání položek do atribut rozšíření <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c7da6-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="c7da6-117">Element rozšíření jsou vytvořené pomocí přidání položek <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="c7da6-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="c7da6-118">Tato rozšíření můžou základní hodnoty, jako je například řetězce, XML serializations objekty rozhraní .NET Framework, nebo z uzlů XML programového ručně.</span><span class="sxs-lookup"><span data-stu-id="c7da6-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="c7da6-119">Následující vzorový kód vytvoří rozšíření element s názvem `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="c7da6-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="c7da6-120">Obor názvů XML pro tento element je prázdný obor názvů ("") a jeho hodnota je textový uzel, který obsahuje text "hello, world!".</span><span class="sxs-lookup"><span data-stu-id="c7da6-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="c7da6-121">Jeden ze způsobů, jak vytvořit komplexní element rozšíření, které se skládají z mnoha vnořených elementů je použití rozhraní API rozhraní .NET Framework pro serializaci (jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány) podle následujících příkladů.</span><span class="sxs-lookup"><span data-stu-id="c7da6-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="c7da6-122">V tomto příkladu `DataContractExtension` a `XmlSerializerExtension` jsou vlastní typy, které jsou napsané pro použití s označuje, že serializátor.</span><span class="sxs-lookup"><span data-stu-id="c7da6-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="c7da6-123"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Třídy lze také vytvořit element rozšíření z <xref:System.Xml.XmlReader> instance.</span><span class="sxs-lookup"><span data-stu-id="c7da6-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="c7da6-124">To umožňuje snadnou integraci s XML, jako zpracování rozhraní API <xref:System.Xml.Linq.XElement> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c7da6-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="c7da6-125">Čtení dat rozšíření</span><span class="sxs-lookup"><span data-stu-id="c7da6-125">Reading Extension Data</span></span>  
 <span data-ttu-id="c7da6-126">Je možné získat hodnoty pro atribut rozšíření vyhledávání atributů v <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekce podle jeho <xref:System.Xml.XmlQualifiedName> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c7da6-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="c7da6-127">Element rozšíření ke kterým se přistupuje pomocí `ReadElementExtensions<T>` metoda.</span><span class="sxs-lookup"><span data-stu-id="c7da6-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="c7da6-128">Je také možné získat `XmlReader` v rozšíření jednotlivý prvek pomocí <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> metoda.</span><span class="sxs-lookup"><span data-stu-id="c7da6-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7da6-129">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="c7da6-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c7da6-130">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7da6-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c7da6-131">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7da6-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c7da6-132">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7da6-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7da6-133">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="c7da6-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7da6-134">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c7da6-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c7da6-135">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c7da6-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7da6-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c7da6-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="c7da6-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7da6-137">See Also</span></span>  
 [<span data-ttu-id="c7da6-138">Rozšíření silného typu</span><span class="sxs-lookup"><span data-stu-id="c7da6-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)  
 [<span data-ttu-id="c7da6-139">Syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="c7da6-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
