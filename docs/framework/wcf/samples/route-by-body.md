---
title: Trasa podle textu
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 4266068bb53e5ae90a05cc6537df2ab9b65b6b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965514"
---
# <a name="route-by-body"></a><span data-ttu-id="ee2ef-102">Trasa podle textu</span><span class="sxs-lookup"><span data-stu-id="ee2ef-102">Route by Body</span></span>
<span data-ttu-id="ee2ef-103">Tato ukázka předvádí, jak implementovat službu, která přijímá objekty zpráv s jakoukoli akcí SOAP.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="ee2ef-104">Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="ee2ef-105">Služba implementuje jednu `Calculate` operaci, která <xref:System.ServiceModel.Channels.Message> přijme parametr <xref:System.ServiceModel.Channels.Message> žádosti a vrátí odpověď.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="ee2ef-106">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee2ef-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ee2ef-108">Ukázka znázorňuje odeslání zprávy na základě obsahu těla.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="ee2ef-109">Integrovaný mechanismus odeslání zprávy modelu služby Windows Communication Foundation (WCF) je založen na akcích zprávy.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="ee2ef-110">Existuje však mnoho existujících webových služeb, které definují všechny své operace pomocí akce = "".</span><span class="sxs-lookup"><span data-stu-id="ee2ef-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="ee2ef-111">Není možné vytvořit službu založenou na jazyce WSDL, která zajišťuje odesílání zpráv s požadavky na základě informací o akci.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="ee2ef-112">Tato ukázka demonstruje kontrakt služby, který je založen na jazyce WSDL (WSDL je obsažen v souboru Service. WSDL, který je součástí ukázky).</span><span class="sxs-lookup"><span data-stu-id="ee2ef-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="ee2ef-113">Kontrakt služby je kalkulačka, podobně jako ta, která se používá v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ee2ef-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="ee2ef-114">`[OperationContract]` Nicméně Určuje `Action=""` pro všechny operace.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="ee2ef-115">Vzhledem k tomu, že služba vyžaduje vlastní chování `DispatchByBodyBehavior` odesílání, aby bylo možné mezi operacemi odesílat zprávy.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="ee2ef-116">Toto chování při zpracování inicializuje `DispatchByBodyElementOperationSelector` selektor vlastních operací s tabulkou názvů operací, které jsou na základě QName odpovídajících prvků obálky.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="ee2ef-117">`DispatchByBodyElementOperationSelector`vyhledá počáteční značku prvního podřízeného textu a vybere operaci pomocí výše zmíněné tabulky.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="ee2ef-118">Klient používá proxy automaticky generovaný ze třídy WSDL exportované službou pomocí [nástroje Svcutil. exe](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ee2ef-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="ee2ef-119">Fakt, že akce všech operací nejsou prázdné, nemá žádný vliv na kód klienta, s výjimkou parametrů akce v automaticky generovaném proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="ee2ef-120">Kód klienta provádí několik výpočtů.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-120">The client code performs several calculations.</span></span> <span data-ttu-id="ee2ef-121">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ee2ef-122">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee2ef-123">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="ee2ef-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ee2ef-124">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee2ef-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ee2ef-125">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee2ef-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ee2ef-126">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee2ef-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee2ef-127">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee2ef-128">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee2ef-129">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee2ef-130">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ee2ef-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
