---
title: "Zjišťování doby provádění operací služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c96aa6752feca637f89ed309d1a5c87cea4a3a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="86d40-102">Zjišťování doby provádění operací služby</span><span class="sxs-lookup"><span data-stu-id="86d40-102">Determining service operation duration</span></span>
<span data-ttu-id="86d40-103">Pokud je povoleno analytické trasování v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikace, doba provádění pro operaci služby se dá snadno určit pomocí protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="86d40-103">If analytic tracing is enabled in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="86d40-104">Toto téma ukazuje, jak určit množství času, které operace služby potřebné k dokončení.</span><span class="sxs-lookup"><span data-stu-id="86d40-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="86d40-105">Určení doba trvání provádění operace služby</span><span class="sxs-lookup"><span data-stu-id="86d40-105">Determining service operation execution duration</span></span>  
  
1.  <span data-ttu-id="86d40-106">Otevřete Prohlížeč událostí kliknutím **spustit**, **spustit**a zadáním `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="86d40-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="86d40-107">Pokud jste nepovolili analytické trasování, rozbalte položku **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace – aplikace** .</span><span class="sxs-lookup"><span data-stu-id="86d40-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="86d40-108">Vyberte **zobrazení**, **ukazují analytické a ladicí protokoly**.</span><span class="sxs-lookup"><span data-stu-id="86d40-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="86d40-109">Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="86d40-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="86d40-110">Ponechte prohlížeče událostí otevřete tak, aby trasování lze zobrazit po spuštění operace služby.</span><span class="sxs-lookup"><span data-stu-id="86d40-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3.  <span data-ttu-id="86d40-111">Dále otevřete [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikace, která zahrnuje službu projekt a projekt klienta, který komunikuje s touto službou.</span><span class="sxs-lookup"><span data-stu-id="86d40-111">Next, open a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="86d40-112">Takové aplikace můžete vytvořit pomocí následujících [kurzu Začínáme](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="86d40-112">You can create such an application by following the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  <span data-ttu-id="86d40-113">Pokud máte [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ukázky nainstalován, můžete otevřít [Začínáme](../../../../../docs/framework/wcf/samples/getting-started-sample.md), obsahující dokončený projekt vytvořený v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="86d40-113">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="86d40-114">Spusťte aplikaci server tak, že stisknete **F5**.</span><span class="sxs-lookup"><span data-stu-id="86d40-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="86d40-115">Spusťte klientská aplikace tak, že pravým tlačítkem myši na **klienta** projekt a výběrem **ladění**, **spustit novou instanci**.</span><span class="sxs-lookup"><span data-stu-id="86d40-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5.  <span data-ttu-id="86d40-116">V prohlížeči událostí aktualizujte protokol analytické a seřaďte události podle ID události.</span><span class="sxs-lookup"><span data-stu-id="86d40-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="86d40-117">Vyhledejte události s ID události [214 – metoda OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span><span class="sxs-lookup"><span data-stu-id="86d40-117">Look for events with Event ID [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span></span>  <span data-ttu-id="86d40-118">Tyto události se zobrazí operací, které byly dokončeny, a jak se doba trvání operace.</span><span class="sxs-lookup"><span data-stu-id="86d40-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="86d40-119">Následující událost zobrazuje dobu trvání operace přidat.</span><span class="sxs-lookup"><span data-stu-id="86d40-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
