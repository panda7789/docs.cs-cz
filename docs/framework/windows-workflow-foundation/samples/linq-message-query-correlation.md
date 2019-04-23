---
title: Korelace dotazů zprávy LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: cc13696cfd8eb2dcdf22fdc067518c8bd55ca32d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973314"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="394e0-102">Korelace dotazů zprávy LINQ</span><span class="sxs-lookup"><span data-stu-id="394e0-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="394e0-103">Tato ukázka předvádí, jak provádět korelace na základě obsahu pomocí vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery> implementace na rozdíl od poskytnuté systémem <xref:System.ServiceModel.XPathMessageQuery>.</span><span class="sxs-lookup"><span data-stu-id="394e0-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="394e0-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="394e0-104">Demonstrates</span></span>  
 <span data-ttu-id="394e0-105">Vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery>, korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="394e0-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="394e0-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="394e0-106">Discussion</span></span>  
 <span data-ttu-id="394e0-107">Tento příklad ukazuje, jak rozšířit z <xref:System.ServiceModel.Dispatcher.MessageQuery> základní třída pro účely korelace.</span><span class="sxs-lookup"><span data-stu-id="394e0-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="394e0-108">Vlastní implementace `LinqMessageQuery`, umožňuje uživatelům poskytnout XName najít ve zprávě pomocí XLinq.</span><span class="sxs-lookup"><span data-stu-id="394e0-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="394e0-109">Data načtená dotazem slouží k tvoří klíč korelace k odeslání zprávy do instance odpovídající pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="394e0-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="394e0-110">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="394e0-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="394e0-111">Tato ukázka poskytuje služby pracovního postupu pomocí koncových bodů HTTP.</span><span class="sxs-lookup"><span data-stu-id="394e0-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="394e0-112">Chcete-li spustit ukázku, správné seznamy ACL adresa URL musí být přidán (naleznete v tématu [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti), buď pomocí sady Visual Studio jako správce nebo spuštěním následujícího příkazu na řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="394e0-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="394e0-113">Ujistěte se, že jsou nahrazeny doména a uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="394e0-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="394e0-114">Po přidání se seznamy ACL adresu URL, pomocí následujícího postupu.</span><span class="sxs-lookup"><span data-stu-id="394e0-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="394e0-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="394e0-115">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="394e0-116">Nastavení více projektů spuštění tak, že kliknete pravým tlačítkem řešení a vyberete **nastavit projekty po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="394e0-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="394e0-117">Přidat **služby** a **klienta** (v uvedeném pořadí) jako více spuštění projektů.</span><span class="sxs-lookup"><span data-stu-id="394e0-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3.  <span data-ttu-id="394e0-118">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="394e0-118">Run the application.</span></span> <span data-ttu-id="394e0-119">Klientské konzoly zobrazuje pracovní postup odeslání objednávky a přijímá id nákupní objednávky a následně potvrzení objednávky.</span><span class="sxs-lookup"><span data-stu-id="394e0-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="394e0-120">V okně služby zobrazí zpracovávaných žádostí.</span><span class="sxs-lookup"><span data-stu-id="394e0-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="394e0-121">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="394e0-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="394e0-122">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="394e0-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="394e0-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="394e0-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="394e0-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="394e0-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
