---
title: Vazba dat v klientovi ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f7a3c4adb1a72a31029da7f73778a5ed407b2f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="5609d-102">Vazba dat v klientovi ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5609d-102">Data Binding in an ASP.NET Client</span></span>
<span data-ttu-id="5609d-103">Tento příklad ukazuje, jak k vytvoření vazby dat vrácených typické [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v aplikaci webových formulářů.</span><span class="sxs-lookup"><span data-stu-id="5609d-103">This sample demonstrates how to bind data returned by a typical [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Web Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5609d-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5609d-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5609d-105">Tento příklad znázorňuje služba, která implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5609d-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5609d-106">Ukázka se skládá z klienta aplikace webových formulářů přístupný z prohlížeče a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="5609d-106">The sample consists of a client Web Forms application accessible from a browser and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="5609d-107">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5609d-107">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5609d-108">Kontrakt je definována `IWeatherService` rozhraní, která zpřístupňuje operace s názvem `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="5609d-108">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="5609d-109">Tato operace přijímá pole města a vrátí pole `WeatherData` objekty, které představují maximální a minimální prognózy teploty pro města.</span><span class="sxs-lookup"><span data-stu-id="5609d-109">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="5609d-110">Na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stránky .aspx klienta, webové DataGrid – ovládací prvek je definován, obsahující grafické znázornění dat vrácený službou.</span><span class="sxs-lookup"><span data-stu-id="5609d-110">On the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="5609d-111">Kód na volání stránky .aspx [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby pro data počasí a vrací data na pole `WeatherData` objekty.</span><span class="sxs-lookup"><span data-stu-id="5609d-111">Code on the .aspx page calls the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="5609d-112">V kolekci DataGrid Určuje, kde pro získání dat z nastavením jeho `DataSource` vlastností do tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="5609d-112">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="5609d-113">Datová vazba dochází při volání v kolekci DataGrid `DataBind` metoda.</span><span class="sxs-lookup"><span data-stu-id="5609d-113">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="5609d-114">Všechny tohoto kódu je součástí.`aspx`</span><span class="sxs-lookup"><span data-stu-id="5609d-114">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="5609d-115">stránky `Page_Load` metoda, tak pokaždé, když uživatel aktualizuje stránku prohlížeče, data se aktualizuje v objektu DataGrid.</span><span class="sxs-lookup"><span data-stu-id="5609d-115">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5609d-116">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="5609d-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5609d-117">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5609d-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5609d-118">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5609d-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5609d-119">Tato ukázka klient je webová stránka, která běží v rámci vývojového webového serveru.</span><span class="sxs-lookup"><span data-stu-id="5609d-119">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="5609d-120">Ke spuštění vývoj webový server, zadejte na příkazovém řádku následující: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span><span class="sxs-lookup"><span data-stu-id="5609d-120">To launch the development Web server, type the following at the command prompt: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="5609d-121">Vyhledejte http://localhost: 8000/klienta.</span><span class="sxs-lookup"><span data-stu-id="5609d-121">Then browse to http://localhost:8000/client.</span></span> <span data-ttu-id="5609d-122">Chcete-li tuto ukázku spustit v počítačích, nahraďte všechny odkazy na `localhost` v souboru Web.config klienta s názvem počítače serveru.</span><span class="sxs-lookup"><span data-stu-id="5609d-122">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5609d-123">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="5609d-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5609d-124">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5609d-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5609d-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5609d-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5609d-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5609d-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a><span data-ttu-id="5609d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="5609d-127">See Also</span></span>
