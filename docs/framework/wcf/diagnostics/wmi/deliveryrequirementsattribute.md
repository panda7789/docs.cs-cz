---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979209"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="c306f-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="c306f-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="c306f-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="c306f-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c306f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c306f-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c306f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c306f-105">Methods</span></span>  
 <span data-ttu-id="c306f-106">Atribut DeliveryRequirementsAttribute Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="c306f-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c306f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c306f-107">Properties</span></span>  
 <span data-ttu-id="c306f-108">Atribut DeliveryRequirementsAttribute třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c306f-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="c306f-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="c306f-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="c306f-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="c306f-110">Data type: string</span></span>  
  
 <span data-ttu-id="c306f-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c306f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c306f-112">Určuje, zda vazba pro službu podporuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="c306f-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="c306f-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="c306f-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="c306f-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="c306f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="c306f-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c306f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c306f-116">Určuje, zda vazba podporuje objednané zprávy.</span><span class="sxs-lookup"><span data-stu-id="c306f-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="c306f-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="c306f-117">TargetContract</span></span>  
 <span data-ttu-id="c306f-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="c306f-118">Data type: string</span></span>  
  
 <span data-ttu-id="c306f-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c306f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c306f-120">Kontrakt, ke kterému se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="c306f-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c306f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c306f-121">Requirements</span></span>  
  
|<span data-ttu-id="c306f-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="c306f-122">MOF</span></span>|<span data-ttu-id="c306f-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c306f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c306f-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="c306f-124">Namespace</span></span>|<span data-ttu-id="c306f-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c306f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c306f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c306f-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
