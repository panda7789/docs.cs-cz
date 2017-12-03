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
ms.openlocfilehash: e8d9e9bfb0967b6c41a3df0015bdd6b4101e0c06
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="49fbd-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... konstruktoru</span><span class="sxs-lookup"><span data-stu-id="49fbd-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="49fbd-103">Vytvoří instanci [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) třídy.</span><span class="sxs-lookup"><span data-stu-id="49fbd-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49fbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49fbd-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49fbd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49fbd-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="49fbd-106">Hodnoty parametru</span><span class="sxs-lookup"><span data-stu-id="49fbd-106">Parameter Values</span></span>  
 <span data-ttu-id="49fbd-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="49fbd-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="49fbd-108">Popisuje operace, která má být provedena v aktivity pracovního postupu, který má být vytvořen, včetně název operace, návratový typ a informace o parametru.</span><span class="sxs-lookup"><span data-stu-id="49fbd-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="49fbd-109">Hodnota tohoto parametru nesmí být **null**.</span><span class="sxs-lookup"><span data-stu-id="49fbd-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="49fbd-110">Ji by měl popisovat synchronní operaci, která používá zprávy smlouvy a použije argument s jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="49fbd-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="49fbd-111">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="49fbd-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="49fbd-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="49fbd-112">*configurationName*</span></span>  
  
 <span data-ttu-id="49fbd-113">Určuje název konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="49fbd-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="49fbd-114">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="49fbd-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="49fbd-115">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="49fbd-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="49fbd-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="49fbd-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="49fbd-117">Určuje obor názvů služby pro operaci.</span><span class="sxs-lookup"><span data-stu-id="49fbd-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="49fbd-118">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="49fbd-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="49fbd-119">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="49fbd-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49fbd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="49fbd-120">See Also</span></span>  
 [<span data-ttu-id="49fbd-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="49fbd-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
