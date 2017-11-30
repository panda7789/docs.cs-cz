---
title: "Datové vazby v klientovi Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 163bd72d9c42680d72c435e8266c75876490a2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a><span data-ttu-id="8d103-102">Datové vazby v klientovi Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d103-102">Data Binding in a Windows Forms Client</span></span>
<span data-ttu-id="8d103-103">Tento příklad znázorňuje způsob vytvoření vazby na data vrácená [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v aplikaci Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8d103-103">This sample demonstrates how to bind to data returned by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Windows Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d103-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="8d103-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>  
  
 <span data-ttu-id="8d103-105">Tento příklad znázorňuje služba, která implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8d103-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8d103-106">Ukázka se skládá z klienta aplikace Windows Forms (.exe) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="8d103-106">The sample consists of a client Windows Forms application (.exe) and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="8d103-107">Kontrakt je definována `IWeatherService` rozhraní, která zpřístupňuje operace s názvem `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="8d103-107">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="8d103-108">Tato operace přijímá pole města a vrátí pole `WeatherData` objekty, které představují maximální a minimální prognózy teploty pro města.</span><span class="sxs-lookup"><span data-stu-id="8d103-108">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="8d103-109">Datové vazby v klientovi v aplikaci Windows Forms dojde.</span><span class="sxs-lookup"><span data-stu-id="8d103-109">The data binding occurs on the client in the Windows Forms application.</span></span> <span data-ttu-id="8d103-110">A `DataGridView` je definována v Návrháři formulářů Windows, což je grafické znázornění dat.</span><span class="sxs-lookup"><span data-stu-id="8d103-110">A `DataGridView` is defined in the Windows Forms designer, which is a graphical representation of the data.</span></span> <span data-ttu-id="8d103-111">Zprostředkovatel s názvem `BindingSource` se také vytvoří.</span><span class="sxs-lookup"><span data-stu-id="8d103-111">An intermediary named `BindingSource` is also created.</span></span> <span data-ttu-id="8d103-112">Zdroj dat `BindingSource` je nastaven na data pole vrácené službou.</span><span class="sxs-lookup"><span data-stu-id="8d103-112">The data source of `BindingSource` is set to the data array returned by the service.</span></span> <span data-ttu-id="8d103-113">Účelem `BindingSource` je poskytnout úroveň dereference mezi data a data zobrazení.</span><span class="sxs-lookup"><span data-stu-id="8d103-113">The purpose of the `BindingSource` is to provide a layer of indirection between the data and the data view.</span></span> <span data-ttu-id="8d103-114">Všechny interakce s daty, jako je například navigace, řazení, filtrování a aktualizace, se provádí pomocí volání `BindingSource` součásti.</span><span class="sxs-lookup"><span data-stu-id="8d103-114">All interaction with the data, such as navigating, sorting, filtering, and updating, is accomplished with calls to the `BindingSource` component.</span></span> <span data-ttu-id="8d103-115">K provedení vazby dat k `DataGridView`, `datasource` z `DataGridView` pak nastavena na `BindingSource` objektu.</span><span class="sxs-lookup"><span data-stu-id="8d103-115">To accomplish data binding to the `DataGridView`, the `datasource` of the `DataGridView` is then set to the `BindingSource` object.</span></span> <span data-ttu-id="8d103-116">Všechna data vrácená z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby se následně zobrazí graficky uživateli.</span><span class="sxs-lookup"><span data-stu-id="8d103-116">All of the data returned from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is then displayed graphically to the user.</span></span>  <span data-ttu-id="8d103-117">Pokaždé, když uživatel klikne na tlačítko, vrácená data se automaticky aktualizuje v vázaného na data `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="8d103-117">Every time the user clicks the button, the returned data is automatically updated in the data-bound `DataGridView`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d103-118">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="8d103-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8d103-119">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d103-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8d103-120">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d103-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8d103-121">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d103-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8d103-122">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="8d103-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d103-123">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8d103-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8d103-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8d103-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d103-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8d103-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a><span data-ttu-id="8d103-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d103-126">See Also</span></span>
