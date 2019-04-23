---
title: Ukázka třídy XMLSerializer
ms.date: 03/30/2017
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
ms.openlocfilehash: 70c6eb07780296672d663c7d5b9259192b189aad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769642"
---
# <a name="xmlserializer-sample"></a><span data-ttu-id="2cd1a-102">Ukázka třídy XMLSerializer</span><span class="sxs-lookup"><span data-stu-id="2cd1a-102">XMLSerializer Sample</span></span>
<span data-ttu-id="2cd1a-103">Tato ukázka předvádí, jak k serializaci a deserializaci typy, které jsou kompatibilní s <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-103">This sample demonstrates how to serialize and deserialize types that are compatible with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="2cd1a-104">Výchozí formátování Windows Communication Foundation (WCF) je <xref:System.Runtime.Serialization.DataContractSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-104">The default Windows Communication Foundation (WCF) formatter is the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span> <span data-ttu-id="2cd1a-105"><xref:System.Xml.Serialization.XmlSerializer> Třídy lze použít k serializaci a deserializaci typy, jestliže <xref:System.Runtime.Serialization.DataContractSerializer> třída se nedá použít.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-105">The <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize and deserialize types when the <xref:System.Runtime.Serialization.DataContractSerializer> class cannot be used.</span></span> <span data-ttu-id="2cd1a-106">To je často případ, kdy mít naprostou kontrolu nad XML se vyžaduje – například pokud část dat musí být atribut XML a není platný element XML.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-106">This is often the case when precise control over the XML is required - for example, if a piece of data must be an XML attribute and not an XML element.</span></span> <span data-ttu-id="2cd1a-107">Také <xref:System.Xml.Serialization.XmlSerializer> často získá automaticky vybrán při vytváření klientů služby bez WCF.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-107">Also, the <xref:System.Xml.Serialization.XmlSerializer> often gets automatically selected when creating clients for non-WCF services.</span></span>  
  
 <span data-ttu-id="2cd1a-108">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="2cd1a-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cd1a-109">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2cd1a-110"><xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.XmlSerializerFormatAttribute> musí vztahovat na rozhraní, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-110">The <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.XmlSerializerFormatAttribute> must be applied to the interface as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="2cd1a-111">Veřejné členy `ComplexNumber` třídy serializují pomocí <xref:System.Xml.Serialization.XmlSerializer> jako atributy ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-111">The public members of `ComplexNumber` class are serialized by <xref:System.Xml.Serialization.XmlSerializer> as XML attributes.</span></span> <span data-ttu-id="2cd1a-112"><xref:System.Runtime.Serialization.DataContractSerializer> Nelze použít k vytvoření tohoto typu XML instance.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-112">The <xref:System.Runtime.Serialization.DataContractSerializer> cannot be used to create this kind of XML instance.</span></span>  
  
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
  
 <span data-ttu-id="2cd1a-113">Implementace služby vypočítá a vrátí odpovídající výsledek – přijímá a vrací hodnoty `ComplexNumber` typu.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-113">The service implementation calculates and returns the appropriate result—accepting and returning values of the `ComplexNumber` type.</span></span>  
  
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
  
 <span data-ttu-id="2cd1a-114">Implementace klienta používá také komplexní čísla.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-114">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="2cd1a-115">Kontrakt služby a datové typy, které jsou definovány ve zdrojovém souboru, který byl vytvořen generatedClient.cs [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-115">Both the service contract and the data types are defined in the generatedClient.cs source file, which was generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="2cd1a-116">Svcutil.exe lze rozpoznat, kdy není serializovatelná podle smlouvy <xref:System.Runtime.Serialization.DataContractSerializer> a vrátí do výstupu `XmlSerializable` typy v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-116">Svcutil.exe can detect when a contract is not serializable by the <xref:System.Runtime.Serialization.DataContractSerializer> and reverts to emitting `XmlSerializable` types in this case.</span></span> <span data-ttu-id="2cd1a-117">Pokud chcete vynutit používání <xref:System.Xml.Serialization.XmlSerializer>, nástroje Svcutil.exe lze předat parametr příkazu /serializer:XmlSerializer (pomocí třídy XmlSerializer).</span><span class="sxs-lookup"><span data-stu-id="2cd1a-117">If you want to force the use of the <xref:System.Xml.Serialization.XmlSerializer>, you can pass the /serializer:XmlSerializer (use XmlSerializer) command option to the Svcutil.exe tool.</span></span>  
  
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
  
 <span data-ttu-id="2cd1a-118">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2cd1a-119">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2cd1a-120">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="2cd1a-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2cd1a-121">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2cd1a-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2cd1a-122">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2cd1a-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2cd1a-123">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2cd1a-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2cd1a-124">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2cd1a-125">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2cd1a-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2cd1a-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2cd1a-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2cd1a-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
