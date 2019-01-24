---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: b63f8917d7af21c165a16bd45a83e774bcec6e1c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551602"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="e35d4-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="e35d4-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="e35d4-103">Vytvoří instanci [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) třídy.</span><span class="sxs-lookup"><span data-stu-id="e35d4-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e35d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e35d4-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e35d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e35d4-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="e35d4-106">Hodnoty parametru</span><span class="sxs-lookup"><span data-stu-id="e35d4-106">Parameter Values</span></span>  
 <span data-ttu-id="e35d4-107">*Popis operationDescription*</span><span class="sxs-lookup"><span data-stu-id="e35d4-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="e35d4-108">Popisuje operace, která má být provedena v aktivity pracovního postupu, který má být vytvořen, včetně název operace, návratový typ a informace o parametru.</span><span class="sxs-lookup"><span data-stu-id="e35d4-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="e35d4-109">Hodnota tohoto parametru nesmí být **null**.</span><span class="sxs-lookup"><span data-stu-id="e35d4-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="e35d4-110">Ji by měl popisovat synchronní operaci, která používá zprávy smlouvy a použije argument s jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="e35d4-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="e35d4-111">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="e35d4-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="e35d4-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="e35d4-112">*configurationName*</span></span>  
  
 <span data-ttu-id="e35d4-113">Určuje název konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e35d4-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="e35d4-114">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e35d4-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="e35d4-115">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="e35d4-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="e35d4-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="e35d4-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="e35d4-117">Určuje obor názvů služby pro operaci.</span><span class="sxs-lookup"><span data-stu-id="e35d4-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="e35d4-118">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e35d4-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="e35d4-119">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="e35d4-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e35d4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e35d4-120">See also</span></span>
- [<span data-ttu-id="e35d4-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="e35d4-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
