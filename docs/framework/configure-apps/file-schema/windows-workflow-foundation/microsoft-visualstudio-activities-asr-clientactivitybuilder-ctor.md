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
ms.openlocfilehash: 0ce9be30182f9181bcb6449529d9b9796aadbc2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133533"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="60ee4-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="60ee4-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="60ee4-103">Vytvoří instanci [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) třídy.</span><span class="sxs-lookup"><span data-stu-id="60ee4-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ee4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60ee4-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60ee4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60ee4-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="60ee4-106">Hodnoty parametru</span><span class="sxs-lookup"><span data-stu-id="60ee4-106">Parameter Values</span></span>  
 <span data-ttu-id="60ee4-107">*Popis operationDescription*</span><span class="sxs-lookup"><span data-stu-id="60ee4-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="60ee4-108">Popisuje operace, která má být provedena v aktivity pracovního postupu, který má být vytvořen, včetně název operace, návratový typ a informace o parametru.</span><span class="sxs-lookup"><span data-stu-id="60ee4-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="60ee4-109">Hodnota tohoto parametru nesmí být **null**.</span><span class="sxs-lookup"><span data-stu-id="60ee4-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="60ee4-110">Ji by měl popisovat synchronní operaci, která používá zprávy smlouvy a použije argument s jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="60ee4-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="60ee4-111">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="60ee4-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="60ee4-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="60ee4-112">*configurationName*</span></span>  
  
 <span data-ttu-id="60ee4-113">Určuje název konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="60ee4-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="60ee4-114">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="60ee4-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="60ee4-115">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="60ee4-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="60ee4-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="60ee4-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="60ee4-117">Určuje obor názvů služby pro operaci.</span><span class="sxs-lookup"><span data-stu-id="60ee4-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="60ee4-118">Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="60ee4-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="60ee4-119">Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="60ee4-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ee4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60ee4-120">See also</span></span>

- [<span data-ttu-id="60ee4-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="60ee4-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
