---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... konstruktoru
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location: Microsoft.VisualStudio.Activities.dll
api_type: Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c50d9754b71386e6809d46cd9666987a704fbf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="d4da4-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... konstruktoru</span><span class="sxs-lookup"><span data-stu-id="d4da4-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="d4da4-103">Vytvoří instanci [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) třídy.</span><span class="sxs-lookup"><span data-stu-id="d4da4-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4da4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4da4-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4da4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4da4-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="d4da4-106">Hodnoty parametru</span><span class="sxs-lookup"><span data-stu-id="d4da4-106">Parameter Values</span></span>  
 <span data-ttu-id="d4da4-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="d4da4-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="d4da4-108">Popisuje operace, která má být provedena v aktivity pracovního postupu, který má být vytvořen, včetně název operace, návratový typ a informace o parametru.</span><span class="sxs-lookup"><span data-stu-id="d4da4-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="d4da4-109">Hodnota tohoto parametru nesmí být **null**.</span><span class="sxs-lookup"><span data-stu-id="d4da4-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="d4da4-110">Ji by měl popisovat synchronní operaci, která používá zprávy smlouvy a použije argument s jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="d4da4-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="d4da4-111">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="d4da4-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="d4da4-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="d4da4-112">*configurationName*</span></span>  
  
 <span data-ttu-id="d4da4-113">Určuje název konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d4da4-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="d4da4-114">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="d4da4-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="d4da4-115">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="d4da4-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="d4da4-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="d4da4-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="d4da4-117">Určuje obor názvů služby pro operaci.</span><span class="sxs-lookup"><span data-stu-id="d4da4-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="d4da4-118">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="d4da4-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="d4da4-119">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="d4da4-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4da4-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4da4-120">See Also</span></span>  
 [<span data-ttu-id="d4da4-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="d4da4-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
