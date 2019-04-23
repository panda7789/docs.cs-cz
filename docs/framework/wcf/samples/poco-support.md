---
title: Podpora objektů POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 86ade3a6b045f6f7c57e4a95936b4f1574b51ff0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334897"
---
# <a name="poco-support"></a><span data-ttu-id="272e5-102">Podpora objektů POCO</span><span class="sxs-lookup"><span data-stu-id="272e5-102">POCO Support</span></span>
<span data-ttu-id="272e5-103">Tato ukázka předvádí, podpora serializaci zrušeno označení typy; To znamená typy, na které nebyly použity atributy serializace, někdy označovány jako obyčejný staré CLR objektů POCO typy.</span><span class="sxs-lookup"><span data-stu-id="272e5-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="272e5-104"><xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat pro všechny veřejné zrušeno označení typy, které mají výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="272e5-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a default constructor.</span></span> <span data-ttu-id="272e5-105">Kontrakty dat umožňuje předání strukturovaná data do a ze služby.</span><span class="sxs-lookup"><span data-stu-id="272e5-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="272e5-106">Další informace o typech zrušeno označení, naleznete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="272e5-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="272e5-107">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale používá komplexní čísla namísto primitivní číselné typy.</span><span class="sxs-lookup"><span data-stu-id="272e5-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="272e5-108">Je také podobné jako [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md) ukázkový, s výjimkou, že <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> nejsou použity atributy.</span><span class="sxs-lookup"><span data-stu-id="272e5-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="272e5-109">Služba je hostována v Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="272e5-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="272e5-110">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="272e5-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="272e5-111">`ComplexNumber` Třída se používá `ServiceContract`.</span><span class="sxs-lookup"><span data-stu-id="272e5-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="272e5-112">`ComplexNumber` Typ nemá <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="272e5-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="272e5-113">Ve výchozím nastavení se serializují všechny veřejné vlastnosti a pole.</span><span class="sxs-lookup"><span data-stu-id="272e5-113">By default, all public properties and fields are serialized.</span></span>  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="272e5-114">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="272e5-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="272e5-115">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="272e5-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="272e5-116">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="272e5-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="272e5-117">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="272e5-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="272e5-118">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="272e5-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="272e5-119">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="272e5-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="272e5-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="272e5-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="272e5-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="272e5-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="272e5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="272e5-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="272e5-123">Serializovatelné typy</span><span class="sxs-lookup"><span data-stu-id="272e5-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
