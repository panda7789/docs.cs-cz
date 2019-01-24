---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 809e9d809bce456c831aab83c7ac19a882b2959b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571321"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="ec101-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="ec101-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="ec101-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="ec101-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec101-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec101-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ec101-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ec101-105">Methods</span></span>  
 <span data-ttu-id="ec101-106">Atribut DeliveryRequirementsAttribute Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ec101-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ec101-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ec101-107">Properties</span></span>  
 <span data-ttu-id="ec101-108">Atribut DeliveryRequirementsAttribute třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ec101-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="ec101-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="ec101-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="ec101-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ec101-110">Data type: string</span></span>  
  
 <span data-ttu-id="ec101-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ec101-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ec101-112">Určuje, zda vazba pro službu podporuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="ec101-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="ec101-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="ec101-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="ec101-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="ec101-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ec101-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ec101-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ec101-116">Určuje, zda vazba podporuje objednané zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec101-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="ec101-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="ec101-117">TargetContract</span></span>  
 <span data-ttu-id="ec101-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ec101-118">Data type: string</span></span>  
  
 <span data-ttu-id="ec101-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ec101-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ec101-120">Kontrakt, ke kterému se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="ec101-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec101-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec101-121">Requirements</span></span>  
  
|<span data-ttu-id="ec101-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="ec101-122">MOF</span></span>|<span data-ttu-id="ec101-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ec101-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ec101-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ec101-124">Namespace</span></span>|<span data-ttu-id="ec101-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ec101-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec101-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec101-126">See also</span></span>
- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
