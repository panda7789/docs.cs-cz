---
title: Ukázka třídy XMLSerializer
ms.date: 03/30/2017
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
ms.openlocfilehash: fd787b5caabf698e471a9ebe4604688bc422e99e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583944"
---
# <a name="xmlserializer-sample"></a><span data-ttu-id="8c7f1-102">Ukázka třídy XMLSerializer</span><span class="sxs-lookup"><span data-stu-id="8c7f1-102">XMLSerializer Sample</span></span>
<span data-ttu-id="8c7f1-103">Tato ukázka demonstruje způsob serializace a deserializace typů, které jsou kompatibilní s rozhraním <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8c7f1-103">This sample demonstrates how to serialize and deserialize types that are compatible with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="8c7f1-104">Výchozím formátovacím modulem Windows Communication Foundation (WCF) je <xref:System.Runtime.Serialization.DataContractSerializer> Třída.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-104">The default Windows Communication Foundation (WCF) formatter is the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span> <span data-ttu-id="8c7f1-105"><xref:System.Xml.Serialization.XmlSerializer>Třídu lze použít k serializaci a deserializaci typů, pokud <xref:System.Runtime.Serialization.DataContractSerializer> třídu nelze použít.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-105">The <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize and deserialize types when the <xref:System.Runtime.Serialization.DataContractSerializer> class cannot be used.</span></span> <span data-ttu-id="8c7f1-106">Často se jedná o případ, kdy je vyžadována přesná kontrola nad XML – například pokud datový kus musí být atribut XML, nikoli XML element.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-106">This is often the case when precise control over the XML is required - for example, if a piece of data must be an XML attribute and not an XML element.</span></span> <span data-ttu-id="8c7f1-107"><xref:System.Xml.Serialization.XmlSerializer>Při vytváření klientů pro jiné služby než WCF se taky často automaticky zvolí.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-107">Also, the <xref:System.Xml.Serialization.XmlSerializer> often gets automatically selected when creating clients for non-WCF services.</span></span>  
  
 <span data-ttu-id="8c7f1-108">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="8c7f1-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c7f1-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8c7f1-110"><xref:System.ServiceModel.ServiceContractAttribute>A <xref:System.ServiceModel.XmlSerializerFormatAttribute> musí se použít na rozhraní, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-110">The <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.XmlSerializerFormatAttribute> must be applied to the interface as shown in the following sample code.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface IXmlSerializerCalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="8c7f1-111">Veřejné členy `ComplexNumber` třídy jsou serializovány pomocí <xref:System.Xml.Serialization.XmlSerializer> atributů XML.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-111">The public members of `ComplexNumber` class are serialized by <xref:System.Xml.Serialization.XmlSerializer> as XML attributes.</span></span> <span data-ttu-id="8c7f1-112"><xref:System.Runtime.Serialization.DataContractSerializer>Nelze použít k vytvoření tohoto typu instance XML.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-112">The <xref:System.Runtime.Serialization.DataContractSerializer> cannot be used to create this kind of XML instance.</span></span>  
  
```csharp  
public class ComplexNumber  
{  
    private double real;  
    private double imaginary;  
  
    [XmlAttribute]  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    [XmlAttribute]  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
    public ComplexNumber()  
    {  
        this.Real = 0;  
        this.Imaginary = 0;  
    }  
  
}  
```  
  
 <span data-ttu-id="8c7f1-113">Implementace služby vypočítá a vrátí příslušný výsledek – přijímá a vrací hodnoty `ComplexNumber` typu.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-113">The service implementation calculates and returns the appropriate result—accepting and returning values of the `ComplexNumber` type.</span></span>  
  
```csharp  
public class XmlSerializerCalculatorService : IXmlSerializerCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
    …  
}  
```  
  
 <span data-ttu-id="8c7f1-114">Implementace klienta také používá složitá čísla.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-114">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="8c7f1-115">Kontrakt služby i datové typy jsou definovány ve zdrojovém souboru generatedClient.cs, který byl vygenerován [nástrojem ServiceModel Metadata Utility (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-115">Both the service contract and the data types are defined in the generatedClient.cs source file, which was generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="8c7f1-116">Svcutil. exe může zjistit, že kontrakt není serializovatelný pomocí <xref:System.Runtime.Serialization.DataContractSerializer> a v tomto případě se vrátí k vygenerování `XmlSerializable` typů.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-116">Svcutil.exe can detect when a contract is not serializable by the <xref:System.Runtime.Serialization.DataContractSerializer> and reverts to emitting `XmlSerializable` types in this case.</span></span> <span data-ttu-id="8c7f1-117">Pokud chcete vynutit použití <xref:System.Xml.Serialization.XmlSerializer> , můžete předat možnost příkazu/Serializer: XmlSerializer (použít XmlSerializer) do nástroje Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-117">If you want to force the use of the <xref:System.Xml.Serialization.XmlSerializer>, you can pass the /serializer:XmlSerializer (use XmlSerializer) command option to the Svcutil.exe tool.</span></span>  
  
```csharp  
// Create a client.  
XmlSerializerCalculatorClient client = new  
                         XmlSerializerCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();  
value1.Real = 1;  
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();  
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,
    result.Real, result.Imaginary);  
    …  
}  
```  
  
 <span data-ttu-id="8c7f1-118">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8c7f1-119">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8c7f1-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8c7f1-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8c7f1-121">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c7f1-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8c7f1-122">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c7f1-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8c7f1-123">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c7f1-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8c7f1-124">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8c7f1-125">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8c7f1-126">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8c7f1-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
