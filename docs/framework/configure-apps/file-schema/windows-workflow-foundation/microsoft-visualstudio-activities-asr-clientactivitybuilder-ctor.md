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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b73274a09ae748cdf1ee33c885de86b1f52c105
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="addb0-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... konstruktoru</span><span class="sxs-lookup"><span data-stu-id="addb0-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="addb0-103">Vytvoří instanci [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) třídy.</span><span class="sxs-lookup"><span data-stu-id="addb0-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="addb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="addb0-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="addb0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="addb0-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="addb0-106">Hodnoty parametru</span><span class="sxs-lookup"><span data-stu-id="addb0-106">Parameter Values</span></span>  
 <span data-ttu-id="addb0-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="addb0-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="addb0-108">Popisuje operace, která má být provedena v aktivity pracovního postupu, který má být vytvořen, včetně název operace, návratový typ a informace o parametru.</span><span class="sxs-lookup"><span data-stu-id="addb0-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="addb0-109">Hodnota tohoto parametru nesmí být **null**.</span><span class="sxs-lookup"><span data-stu-id="addb0-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="addb0-110">Ji by měl popisovat synchronní operaci, která používá zprávy smlouvy a použije argument s jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="addb0-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="addb0-111">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="addb0-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="addb0-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="addb0-112">*configurationName*</span></span>  
  
 <span data-ttu-id="addb0-113">Určuje název konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="addb0-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="addb0-114">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="addb0-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="addb0-115">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="addb0-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="addb0-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="addb0-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="addb0-117">Určuje obor názvů služby pro operaci.</span><span class="sxs-lookup"><span data-stu-id="addb0-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="addb0-118">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="addb0-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="addb0-119">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="addb0-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="addb0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="addb0-120">See Also</span></span>  
 [<span data-ttu-id="addb0-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="addb0-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
