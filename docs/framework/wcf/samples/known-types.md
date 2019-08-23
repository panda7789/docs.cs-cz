---
title: Známé typy
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: ebcf5e4a1e6d587a3047e3faffb03847715f7a85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952862"
---
# <a name="known-types"></a><span data-ttu-id="fb3e9-102">Známé typy</span><span class="sxs-lookup"><span data-stu-id="fb3e9-102">Known Types</span></span>
<span data-ttu-id="fb3e9-103">Tato ukázka předvádí, jak zadat informace o odvozených typech v kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="fb3e9-104">Kontrakty dat umožňují předat strukturovaná data službám a ze služeb.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="fb3e9-105">V objektově orientovaném programování lze použít typ, který dědí z jiného typu místo původní typ.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="fb3e9-106">V programování orientovaném na služby se schémata místo typů sdělují a proto se nezachuje vztah mezi typy.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="fb3e9-107"><xref:System.Runtime.Serialization.KnownTypeAttribute> Atribut umožňuje zahrnutí informací o odvozených typech do kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="fb3e9-108">Pokud se tento mechanismus nepoužívá, nelze odeslat ani přijmout odvozený typ, kde je očekáván základní typ.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb3e9-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fb3e9-110">Kontrakt služby pro službu používá složitá čísla, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
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
  
 <span data-ttu-id="fb3e9-111">A je použita na`ComplexNumber` třídu, která určuje, která pole třídy lze předat mezi klientem a službu. <xref:System.Runtime.Serialization.DataMemberAttribute> <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="fb3e9-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="fb3e9-112">Odvozenou `ComplexNumberWithMagnitude` třídu lze použít `ComplexNumber`místo.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="fb3e9-113"><xref:System.Runtime.Serialization.KnownTypeAttribute> Atribut`ComplexNumber` typu označuje toto.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
[KnownType(typeof(ComplexNumberWithMagnitude))]  
public class ComplexNumber  
{  
    [DataMember]  
    public double Real = 0.0D;  
    [DataMember]  
    public double Imaginary = 0.0D;  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
 <span data-ttu-id="fb3e9-114">Typ je odvozen z `ComplexNumber` , `Magnitude`ale přidává dalšího datového člena. `ComplexNumberWithMagnitude`</span><span class="sxs-lookup"><span data-stu-id="fb3e9-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumberWithMagnitude : ComplexNumber  
{  
    public ComplexNumberWithMagnitude(double real, double imaginary) :  
        base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary*Imaginary  + Real*Real); }  
        set { throw new NotImplementedException(); }  
    }  
}  
```  
  
 <span data-ttu-id="fb3e9-115">Chcete-li předvést funkce známých typů, je služba implementována způsobem, který vrátí `ComplexNumberWithMagnitude` pouze pro sčítání a odčítání.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="fb3e9-116">(I když kontrakt specifikuje `ComplexNumber`, to je povoleno `KnownTypeAttribute` z důvodu atributu).</span><span class="sxs-lookup"><span data-stu-id="fb3e9-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="fb3e9-117">Násobení a dělení stále vracejí základní `ComplexNumber` typ.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
```csharp
public class DataContractCalculatorService : IDataContractCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real,  
                                      n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real,   
                                 n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        //Return the base type.  
        return new ComplexNumber(real1 + real2, imaginary1 +   
                                                  imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real,   
                                     -1*n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
        //Return the base type.  
        return new ComplexNumber(numerator.Real / denominator.Real,  
                                             numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="fb3e9-118">V klientovi je ve zdrojovém souboru generatedClient.cs, který je generován [nástrojem ServiceModel Metadata Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z metadat služby, definovaná jak kontrakt služby, tak kontrakt dat.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="fb3e9-119">Vzhledem k tomu, že je `ComplexNumber` `ComplexNumberWithMagnitude` atributzadánvkontraktudatslužby,klientmůžepřipoužíváníslužby<xref:System.Runtime.Serialization.KnownTypeAttribute> získat třídy i.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="fb3e9-120">Klient zjistí, zda `ComplexNumberWithMagnitude` má a vygeneruje příslušný výstup:</span><span class="sxs-lookup"><span data-stu-id="fb3e9-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
```csharp
// Create a client  
DataContractCalculatorClient client =   
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber() { real = 1, imaginary = 2 };  
ComplexNumber value2 = new ComplexNumber() { real = 3, imaginary = 4 };  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.real, value1.imaginary, value2.real, value2.imaginary,  
    result.real, result.imaginary);  
if (result is ComplexNumberWithMagnitude)  
{  
    Console.WriteLine("Magnitude: {0}",   
        ((ComplexNumberWithMagnitude)result).Magnitude);  
}  
else  
{  
    Console.WriteLine("No magnitude was sent from the service");  
}  
```  
  
 <span data-ttu-id="fb3e9-121">Při spuštění ukázky se žádosti a odpovědi na operaci zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="fb3e9-122">Všimněte si, že velikost je vytištěna pro sčítání a odčítání, ale nikoli pro násobení a dělení z důvodu způsobu implementace služby.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="fb3e9-123">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
    Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fb3e9-124">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="fb3e9-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fb3e9-125">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fb3e9-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fb3e9-126">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fb3e9-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fb3e9-127">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fb3e9-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb3e9-128">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fb3e9-129">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fb3e9-130">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fb3e9-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="fb3e9-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
