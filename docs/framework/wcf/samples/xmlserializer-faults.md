---
title: XmlSerializer – zpracování chyb
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: c800b23ca5f3589ba3a99b88471afe5b4e5a62bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959640"
---
# <a name="xmlserializer-faults"></a><span data-ttu-id="0d599-102">XmlSerializer – zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="0d599-102">XmlSerializer Faults</span></span>
<span data-ttu-id="0d599-103">Ukázka smlouvy o <xref:System.Xml.Serialization.XmlSerializer> selháníukazuje,jakkomunikovatinformaceochybězeslužby<xref:System.Xml.Serialization.XmlSerializer> klientovi pomocí nástroje.</span><span class="sxs-lookup"><span data-stu-id="0d599-103">The <xref:System.Xml.Serialization.XmlSerializer> fault contract sample demonstrates how to communicate error information from a service to a client using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="0d599-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)s nějakým dalším kódem přidaným do služby pro převod vnitřní výjimky na chybu.</span><span class="sxs-lookup"><span data-stu-id="0d599-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="0d599-105">Klient se pokusí provést dělení nulou, aby vynutil chybový stav služby.</span><span class="sxs-lookup"><span data-stu-id="0d599-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d599-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0d599-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0d599-107">Smlouva kalkulačky byla upravena tak, aby <xref:System.ServiceModel.FaultContractAttribute> obsahovala, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="0d599-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span> <span data-ttu-id="0d599-108">Také se používá k povolení serializace <xref:System.Xml.Serialization.XmlSerializer>pomocí. <xref:System.ServiceModel.XmlSerializerFormatAttribute></span><span class="sxs-lookup"><span data-stu-id="0d599-108">Also, the <xref:System.ServiceModel.XmlSerializerFormatAttribute> is used to enable serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="0d599-109">Vlastnost je nastavena na `true` hodnotu u tohoto atributu, který instruuje serializátor k použití <xref:System.Xml.Serialization.XmlSerializer> pro čtení a zápis chyb. <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A></span><span class="sxs-lookup"><span data-stu-id="0d599-109">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> property is set to `true` on this attribute, which instructs the serializer to use the <xref:System.Xml.Serialization.XmlSerializer> for reading and writing faults.</span></span>  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
  
    [OperationContract]  
    int Subtract(int n1, int n2);  
  
    [OperationContract]  
    int Multiply(int n1, int n2);  
  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="0d599-110">Při generování kódu pro klientský proxy server je nutné použít příznak **/UseSerializerForFaults** pro nástroj pro [Svcutil metadat (. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0d599-110">When generating code for the client proxy, you must apply the **/UseSerializerForFaults** flag to [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d599-111">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="0d599-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0d599-112">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d599-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0d599-113">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d599-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0d599-114">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d599-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d599-115">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="0d599-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0d599-116">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="0d599-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0d599-117">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="0d599-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0d599-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0d599-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a><span data-ttu-id="0d599-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d599-119">See also</span></span>

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
