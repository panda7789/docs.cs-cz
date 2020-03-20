---
title: Trasa podle textu
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144185"
---
# <a name="route-by-body"></a><span data-ttu-id="bd656-102">Trasa podle textu</span><span class="sxs-lookup"><span data-stu-id="bd656-102">Route by Body</span></span>
<span data-ttu-id="bd656-103">Tato ukázka ukazuje, jak implementovat službu, která přijímá objekty zprávy s jakoukoli akcí SOAP.</span><span class="sxs-lookup"><span data-stu-id="bd656-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="bd656-104">Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="bd656-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="bd656-105">Služba implementuje `Calculate` jednu operaci, <xref:System.ServiceModel.Channels.Message> která přijímá <xref:System.ServiceModel.Channels.Message> parametr požadavku a vrací odpověď.</span><span class="sxs-lookup"><span data-stu-id="bd656-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="bd656-106">V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="bd656-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd656-107">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="bd656-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bd656-108">Ukázka ukazuje odeslání zprávy na základě obsahu těla.</span><span class="sxs-lookup"><span data-stu-id="bd656-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="bd656-109">Vestavěný Windows Communication Foundation (WCF) mechanismus odesílání zpráv modelu služby je založen na akcích zprávy.</span><span class="sxs-lookup"><span data-stu-id="bd656-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="bd656-110">Existuje však mnoho existujících webových služeb, které definují všechny své operace s Action="".</span><span class="sxs-lookup"><span data-stu-id="bd656-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="bd656-111">Není možné vytvořit službu založenou na WSDL, která udržuje odesílání zpráv požadavků na základě informací akce.</span><span class="sxs-lookup"><span data-stu-id="bd656-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="bd656-112">Tato ukázka ukazuje servisní smlouvy, která je založena na WSDL (WSDL je obsažen v Service.wsdl, který je součástí vzorku).</span><span class="sxs-lookup"><span data-stu-id="bd656-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="bd656-113">Servisní smlouva je Kalkulačka, podobná té, která se používá v [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="bd656-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="bd656-114">Nicméně `[OperationContract]` určuje `Action=""` pro všechny operace.</span><span class="sxs-lookup"><span data-stu-id="bd656-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="bd656-115">Dané smlouvy, služba vyžaduje vlastní `DispatchByBodyBehavior` odeslání chování povolit zprávy, které mají být odesílány mezi operacemi.</span><span class="sxs-lookup"><span data-stu-id="bd656-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="bd656-116">Toto chování odeslání inicializuje `DispatchByBodyElementOperationSelector` vlastní selektor operace s tabulkou názvů operací zakódovaných QName příslušných prvků obálky.</span><span class="sxs-lookup"><span data-stu-id="bd656-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="bd656-117">`DispatchByBodyElementOperationSelector`vyhledá počáteční značku první podřízené položky těla a vybere operaci pomocí výše uvedené tabulky.</span><span class="sxs-lookup"><span data-stu-id="bd656-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="bd656-118">Klient používá proxy automaticky generovaný z WSDL exportované službou pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bd656-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="bd656-119">Skutečnost, že akce všech operací jsou prázdné nemá žádný vliv na kód klienta, s výjimkou Action parametry v automaticky generované proxy.</span><span class="sxs-lookup"><span data-stu-id="bd656-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="bd656-120">Kód klienta provádí několik výpočtů.</span><span class="sxs-lookup"><span data-stu-id="bd656-120">The client code performs several calculations.</span></span> <span data-ttu-id="bd656-121">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="bd656-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bd656-122">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="bd656-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd656-123">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="bd656-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bd656-124">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd656-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bd656-125">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd656-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="bd656-126">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd656-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bd656-127">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="bd656-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd656-128">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="bd656-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bd656-129">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bd656-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd656-130">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bd656-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
