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
ms.openlocfilehash: 99f2eb9447bdf43cb57cfe86f35d2c09044ed470
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69947618"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="0719c-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="0719c-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="0719c-103">Vytvoří instanci třídy [Microsoft. VisualStudio. Activities. ASR. ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) .</span><span class="sxs-lookup"><span data-stu-id="0719c-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0719c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0719c-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0719c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0719c-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="0719c-106">Hodnoty parametru</span><span class="sxs-lookup"><span data-stu-id="0719c-106">Parameter Values</span></span>  
 <span data-ttu-id="0719c-107">*Name popisu OperationDescription*</span><span class="sxs-lookup"><span data-stu-id="0719c-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="0719c-108">Popisuje operace, která má být provedena v aktivity pracovního postupu, který má být vytvořen, včetně název operace, návratový typ a informace o parametru.</span><span class="sxs-lookup"><span data-stu-id="0719c-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="0719c-109">Hodnota tohoto parametru nesmí být **null**.</span><span class="sxs-lookup"><span data-stu-id="0719c-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="0719c-110">Ji by měl popisovat synchronní operaci, která používá zprávy smlouvy a použije argument s jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="0719c-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="0719c-111">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="0719c-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="0719c-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="0719c-112">*configurationName*</span></span>  
  
 <span data-ttu-id="0719c-113">Určuje název konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="0719c-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="0719c-114">Hodnota tohoto parametru nesmí být **null** ani prázdná.</span><span class="sxs-lookup"><span data-stu-id="0719c-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="0719c-115">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="0719c-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="0719c-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="0719c-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="0719c-117">Určuje obor názvů služby pro operaci.</span><span class="sxs-lookup"><span data-stu-id="0719c-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="0719c-118">Hodnota tohoto parametru nesmí být **null** ani prázdná.</span><span class="sxs-lookup"><span data-stu-id="0719c-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="0719c-119">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="0719c-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0719c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0719c-120">See also</span></span>

- [<span data-ttu-id="0719c-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="0719c-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
