---
title: Podpora objektů POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: a9f8d185c58b22e68f7a8c11954e0e534c4bd48f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600461"
---
# <a name="poco-support"></a><span data-ttu-id="811ba-102">Podpora objektů POCO</span><span class="sxs-lookup"><span data-stu-id="811ba-102">POCO Support</span></span>
<span data-ttu-id="811ba-103">Tato ukázka demonstruje podporu serializace pro neoznačené typy; To znamená, že typy, které atributy serializace nebyly aplikovány, se někdy označují jako prosté staré typy objektů CLR (POCO).</span><span class="sxs-lookup"><span data-stu-id="811ba-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="811ba-104"><xref:System.Runtime.Serialization.DataContractSerializer>Odvodí kontrakt dat pro všechny veřejné neoznačené typy, které mají konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="811ba-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="811ba-105">Kontrakty dat umožňují předat strukturovaná data službám a ze služeb.</span><span class="sxs-lookup"><span data-stu-id="811ba-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="811ba-106">Další informace o neoznačených typech naleznete v tématu [Serializovatelné typy](../feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="811ba-106">For more information about unmarked types, see [Serializable Types](../feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="811ba-107">Tato ukázka je založena na [Začínáme](getting-started-sample.md), ale používá složitá čísla namísto primitivních číselných typů.</span><span class="sxs-lookup"><span data-stu-id="811ba-107">This sample is based on the [Getting Started](getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="811ba-108">Je také podobný ukázce [základního data kontraktu](basic-data-contract.md) s tím rozdílem, že <xref:System.Runtime.Serialization.DataContractAttribute> nejsou <xref:System.Runtime.Serialization.DataMemberAttribute> použity atributy a.</span><span class="sxs-lookup"><span data-stu-id="811ba-108">It is also similar to the [Basic Data Contract](basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="811ba-109">Služba je hostována službou Internetová informační služba (IIS) a klientem je Konzolová aplikace (. exe).</span><span class="sxs-lookup"><span data-stu-id="811ba-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="811ba-110">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="811ba-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="811ba-111">`ComplexNumber`Třída se používá v `ServiceContract` .</span><span class="sxs-lookup"><span data-stu-id="811ba-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="811ba-112">`ComplexNumber`Typ nemá <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atributy a, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="811ba-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="811ba-113">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti a pole.</span><span class="sxs-lookup"><span data-stu-id="811ba-113">By default, all public properties and fields are serialized.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="811ba-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="811ba-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="811ba-115">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="811ba-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="811ba-116">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="811ba-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="811ba-117">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="811ba-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="811ba-118">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="811ba-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="811ba-119">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="811ba-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="811ba-120">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="811ba-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="811ba-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="811ba-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="811ba-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="811ba-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="811ba-123">Serializovatelné typy</span><span class="sxs-lookup"><span data-stu-id="811ba-123">Serializable Types</span></span>](../feature-details/serializable-types.md)
