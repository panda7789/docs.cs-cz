---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 172f7df4f028c1ddc0f5565e95291e857ee6fa1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="cf05a-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="cf05a-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="cf05a-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="cf05a-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf05a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf05a-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cf05a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cf05a-105">Methods</span></span>  
 <span data-ttu-id="cf05a-106">Třída Atribut DeliveryRequirementsAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="cf05a-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cf05a-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cf05a-107">Properties</span></span>  
 <span data-ttu-id="cf05a-108">Atribut DeliveryRequirementsAttribute třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cf05a-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="cf05a-109">Atribut QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="cf05a-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="cf05a-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="cf05a-110">Data type: string</span></span>  
  
 <span data-ttu-id="cf05a-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cf05a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf05a-112">Určuje, zda vazby pro službu podporuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="cf05a-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="cf05a-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="cf05a-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="cf05a-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="cf05a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="cf05a-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cf05a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf05a-116">Určuje, zda vazby podporuje seřazené zprávy.</span><span class="sxs-lookup"><span data-stu-id="cf05a-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="cf05a-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="cf05a-117">TargetContract</span></span>  
 <span data-ttu-id="cf05a-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="cf05a-118">Data type: string</span></span>  
  
 <span data-ttu-id="cf05a-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cf05a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf05a-120">Kontrakt, na který se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="cf05a-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf05a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf05a-121">Requirements</span></span>  
  
|<span data-ttu-id="cf05a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cf05a-122">MOF</span></span>|<span data-ttu-id="cf05a-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cf05a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cf05a-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="cf05a-124">Namespace</span></span>|<span data-ttu-id="cf05a-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cf05a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf05a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf05a-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
