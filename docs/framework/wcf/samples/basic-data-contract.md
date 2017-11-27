---
title: "Základní kontrakt dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Data Contract
ms.assetid: b124e9e0-cb73-4ae0-b9c3-e6cdf5eced98
caps.latest.revision: "37"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f428953fe6803f1ade4f4947f71b0e1360fdb96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="basic-data-contract"></a><span data-ttu-id="ae30f-102">Základní kontrakt dat</span><span class="sxs-lookup"><span data-stu-id="ae30f-102">Basic Data Contract</span></span>
<span data-ttu-id="ae30f-103">Tento příklad znázorňuje způsob implementace kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="ae30f-103">This sample demonstrates how to implement a data contract.</span></span> <span data-ttu-id="ae30f-104">Kontrakty dat umožňují předat strukturovaných dat do a ze služby.</span><span class="sxs-lookup"><span data-stu-id="ae30f-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="ae30f-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , ale místo základní číselnými typy používá komplexní čísla.</span><span class="sxs-lookup"><span data-stu-id="ae30f-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) but uses complex numbers instead of basic numeric types.</span></span>  
  
 <span data-ttu-id="ae30f-106">V této ukázce služba je hostovaná Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="ae30f-106">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae30f-107">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ae30f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ae30f-108">Kontrakt služby pro tuto službu využívá komplexní čísla, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="ae30f-108">The service contract for this service uses complex numbers, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="ae30f-109"><xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> definici byly použity atributy `ComplexNumber` třída k označení, která pole třídy lze předat prostřednictvím sítě mezi klientem a službou, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="ae30f-109">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes have been applied to the definition of the `ComplexNumber` class to indicate which fields of the class can be passed over the wire between the client and the service, as shown in the following sample code.</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
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
  
 <span data-ttu-id="ae30f-110">Implementace služby vypočítá a vrátí odpovídající výsledek, přijetí a vrací počet `ComplexNumber` typu.</span><span class="sxs-lookup"><span data-stu-id="ae30f-110">The service implementation calculates and returns the appropriate result, accepting and returning numbers of the `ComplexNumber` type.</span></span>  
  
```  
// This is the service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real - n2.Real, n1.Imaginary -   
                                                     n2.Imaginary);  
    }  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        return new ComplexNumber(real1 + real2, imaginary1 +   
                                                 imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
         ComplexNumber conjugate =   
              new ComplexNumber(n2.Real, -1*n2.Imaginary);  
         ComplexNumber numerator = Multiply(n1, conjugate);  
         ComplexNumber denominator = Multiply(n2, conjugate);  
         return new ComplexNumber(numerator.Real / denominator.Real,  
                                               numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="ae30f-111">Implementace klienta používá také komplexní čísla.</span><span class="sxs-lookup"><span data-stu-id="ae30f-111">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="ae30f-112">Kontrakt služby a kontrakt dat jsou definovány v souboru generatedClient.cs zdroj, který je generován [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="ae30f-112">Both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span>  
  
```  
// Create a client.  
DataContractCalculatorClient client = new DataContractCalculatorClient();  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();   
value1.Real = 1;   
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();   
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = proxy.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
      value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,   
      result.Real, result.Imaginary);   
    …  
}  
```  
  
 <span data-ttu-id="ae30f-113">Když spustíte ukázku, požadavky a odpovědi operace se zobrazují v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="ae30f-113">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="ae30f-114">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="ae30f-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae30f-115">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ae30f-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ae30f-116">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae30f-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ae30f-117">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae30f-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ae30f-118">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae30f-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae30f-119">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="ae30f-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ae30f-120">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ae30f-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ae30f-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ae30f-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ae30f-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ae30f-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\Basic`  
  
## <a name="see-also"></a><span data-ttu-id="ae30f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae30f-123">See Also</span></span>
