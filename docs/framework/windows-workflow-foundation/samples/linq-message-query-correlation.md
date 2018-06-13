---
title: Korelace dotazu LINQ zprávy
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 5b215764f7e02f07873f63872f4ac8c3fcaffbcc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515840"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="32302-102">Korelace dotazu LINQ zprávy</span><span class="sxs-lookup"><span data-stu-id="32302-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="32302-103">Tento příklad znázorňuje, jak to provést pomocí vlastní korelace na základě obsahu <xref:System.ServiceModel.Dispatcher.MessageQuery> implementace oproti poskytované systémem <xref:System.ServiceModel.XPathMessageQuery>.</span><span class="sxs-lookup"><span data-stu-id="32302-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="32302-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="32302-104">Demonstrates</span></span>  
 <span data-ttu-id="32302-105">Vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery>, korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="32302-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="32302-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="32302-106">Discussion</span></span>  
 <span data-ttu-id="32302-107">Tento příklad ukazuje, jak rozšířit z <xref:System.ServiceModel.Dispatcher.MessageQuery> základní třída pro účely korelace.</span><span class="sxs-lookup"><span data-stu-id="32302-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="32302-108">Vlastní implementace `LinqMessageQuery`, umožňuje uživatelům poskytnout XName najít ve zprávě pomocí XLinq.</span><span class="sxs-lookup"><span data-stu-id="32302-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="32302-109">Data načtená v dotazu se používá k korelace klíče k odeslání zprávy a pokuste se k instanci pracovního postupu vhodné.</span><span class="sxs-lookup"><span data-stu-id="32302-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="32302-110">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="32302-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="32302-111">Tato ukázka zpřístupní služby pracovního postupu pomocí koncových bodů protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="32302-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="32302-112">Použít tuto ukázku, správné seznamy ACL adresa URL musí být přidán (viz [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti), spuštění sady Visual Studio jako správce, nebo spuštěním následujícího příkazu řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="32302-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="32302-113">Zajistěte, aby uživatelské jméno a doména jsou nahrazována.</span><span class="sxs-lookup"><span data-stu-id="32302-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="32302-114">Jakmile se přidají adresy URL seznamy ACL, použijte následující postup.</span><span class="sxs-lookup"><span data-stu-id="32302-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="32302-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="32302-115">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="32302-116">Pravým tlačítkem myši řešení a výběrem nastavit více projektů spuštění **nastavit projekty po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="32302-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="32302-117">Přidat **služby** a **klienta** (v tomto pořadí) jako více projektů spuštění.</span><span class="sxs-lookup"><span data-stu-id="32302-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3.  <span data-ttu-id="32302-118">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="32302-118">Run the application.</span></span> <span data-ttu-id="32302-119">Konzole klienta ukazuje pracovní postup odesílání pořadí a přijetí id pořadí nákupu a následně potvrzení pořadí.</span><span class="sxs-lookup"><span data-stu-id="32302-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="32302-120">Okno služby zobrazí zpracovávaných požadavků.</span><span class="sxs-lookup"><span data-stu-id="32302-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="32302-121">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="32302-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="32302-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="32302-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="32302-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="32302-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32302-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="32302-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
