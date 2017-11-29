---
title: Trasa podle textu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: efbf38d562b120308abc6fc4514a9d17ef608b51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="route-by-body"></a><span data-ttu-id="3010e-102">Trasa podle textu</span><span class="sxs-lookup"><span data-stu-id="3010e-102">Route by Body</span></span>
<span data-ttu-id="3010e-103">Tento příklad znázorňuje způsob implementace služba, která přijímá zprávy objekty s žádnou akci protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3010e-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="3010e-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="3010e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="3010e-105">Služba implementuje jedné `Calculate` operace, která přijímá <xref:System.ServiceModel.Channels.Message> požadavků parametr a vrátí <xref:System.ServiceModel.Channels.Message> odpovědi.</span><span class="sxs-lookup"><span data-stu-id="3010e-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="3010e-106">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="3010e-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3010e-107">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3010e-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3010e-108">Ukázka ukazuje odesílání zpráv na základě obsahu textu.</span><span class="sxs-lookup"><span data-stu-id="3010e-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="3010e-109">Integrované [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanismu odesílání zpráv model služby je na základě zprávy akce.</span><span class="sxs-lookup"><span data-stu-id="3010e-109">The built-in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="3010e-110">Existují však mnoho existujících webových služeb, které definují všechny své operace pomocí akce = "".</span><span class="sxs-lookup"><span data-stu-id="3010e-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="3010e-111">Není možné vytvořit služby založené na jazyce WSDL, který udržuje odeslání zprávy s požadavky na informace o akci.</span><span class="sxs-lookup"><span data-stu-id="3010e-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="3010e-112">Tento příklad znázorňuje kontraktu služby, která je založena na WSDL (schématu WSDL je součástí Service.wsdl, který se dodává s ukázkou).</span><span class="sxs-lookup"><span data-stu-id="3010e-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="3010e-113">Kontrakt služby je kalkulačky, podobně jako používaný v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3010e-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="3010e-114">Ale `[OperationContract]` Určuje `Action=""` pro všechny operace.</span><span class="sxs-lookup"><span data-stu-id="3010e-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
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
  
 <span data-ttu-id="3010e-115">Zadána kontraktu služby vyžaduje vlastní odesílání chování `DispatchByBodyBehavior` umožňující zpráv, které mají být odeslány mezi operacemi.</span><span class="sxs-lookup"><span data-stu-id="3010e-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="3010e-116">Toto chování odesílání inicializuje `DispatchByBodyElementOperationSelector` selektor vlastní operace s tabulkou názvů operace s klíči QName elementů příslušných obálku.</span><span class="sxs-lookup"><span data-stu-id="3010e-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="3010e-117">`DispatchByBodyElementOperationSelector`u počáteční značky prvního podřízeného obsahu vyhledá a vybere operaci v tabulce výše.</span><span class="sxs-lookup"><span data-stu-id="3010e-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="3010e-118">Klient používá automaticky generovaný z WSDL exportovali pomocí služby proxy [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3010e-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="3010e-119">Skutečnost, že akce všechny operace jsou prázdné nemá žádný vliv na kód klienta, s výjimkou parametrů akce v automaticky generovaných proxy.</span><span class="sxs-lookup"><span data-stu-id="3010e-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="3010e-120">Kód klienta provede několik výpočtů.</span><span class="sxs-lookup"><span data-stu-id="3010e-120">The client code performs several calculations.</span></span> <span data-ttu-id="3010e-121">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="3010e-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3010e-122">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="3010e-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3010e-123">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="3010e-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3010e-124">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3010e-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3010e-125">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3010e-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3010e-126">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3010e-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3010e-127">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="3010e-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3010e-128">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3010e-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3010e-129">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3010e-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3010e-130">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3010e-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a><span data-ttu-id="3010e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="3010e-131">See Also</span></span>
