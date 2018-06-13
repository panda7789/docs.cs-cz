---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: d294ba4f14472012b9e311ee53742633b5173f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485782"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="c47eb-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="c47eb-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="c47eb-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="c47eb-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c47eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c47eb-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c47eb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c47eb-105">Methods</span></span>  
 <span data-ttu-id="c47eb-106">Třída Atribut DeliveryRequirementsAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="c47eb-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c47eb-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c47eb-107">Properties</span></span>  
 <span data-ttu-id="c47eb-108">Atribut DeliveryRequirementsAttribute třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c47eb-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="c47eb-109">Atribut QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="c47eb-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="c47eb-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="c47eb-110">Data type: string</span></span>  
  
 <span data-ttu-id="c47eb-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c47eb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c47eb-112">Určuje, zda vazby pro službu podporuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="c47eb-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="c47eb-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="c47eb-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="c47eb-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="c47eb-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="c47eb-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c47eb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c47eb-116">Určuje, zda vazby podporuje seřazené zprávy.</span><span class="sxs-lookup"><span data-stu-id="c47eb-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="c47eb-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="c47eb-117">TargetContract</span></span>  
 <span data-ttu-id="c47eb-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="c47eb-118">Data type: string</span></span>  
  
 <span data-ttu-id="c47eb-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c47eb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c47eb-120">Kontrakt, na který se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="c47eb-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c47eb-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c47eb-121">Requirements</span></span>  
  
|<span data-ttu-id="c47eb-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c47eb-122">MOF</span></span>|<span data-ttu-id="c47eb-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c47eb-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c47eb-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="c47eb-124">Namespace</span></span>|<span data-ttu-id="c47eb-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c47eb-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c47eb-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c47eb-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
