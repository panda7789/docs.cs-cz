---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101774"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="25b38-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="25b38-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="25b38-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="25b38-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25b38-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="25b38-105">Metody</span><span class="sxs-lookup"><span data-stu-id="25b38-105">Methods</span></span>  
 <span data-ttu-id="25b38-106">Atribut DeliveryRequirementsAttribute Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="25b38-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="25b38-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25b38-107">Properties</span></span>  
 <span data-ttu-id="25b38-108">Atribut DeliveryRequirementsAttribute třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="25b38-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="25b38-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="25b38-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="25b38-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="25b38-110">Data type: string</span></span>  
  
 <span data-ttu-id="25b38-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="25b38-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25b38-112">Určuje, zda vazba pro službu podporuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="25b38-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="25b38-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="25b38-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="25b38-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="25b38-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="25b38-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="25b38-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25b38-116">Určuje, zda vazba podporuje objednané zprávy.</span><span class="sxs-lookup"><span data-stu-id="25b38-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="25b38-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="25b38-117">TargetContract</span></span>  
 <span data-ttu-id="25b38-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="25b38-118">Data type: string</span></span>  
  
 <span data-ttu-id="25b38-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="25b38-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25b38-120">Kontrakt, ke kterému se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="25b38-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25b38-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25b38-121">Requirements</span></span>  
  
|<span data-ttu-id="25b38-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="25b38-122">MOF</span></span>|<span data-ttu-id="25b38-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="25b38-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="25b38-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="25b38-124">Namespace</span></span>|<span data-ttu-id="25b38-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="25b38-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25b38-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25b38-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
