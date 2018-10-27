---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 7bfc03299fffc8070a7d8a4b3885706ea861bdf6
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50042893"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="b8cdb-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="b8cdb-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="b8cdb-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="b8cdb-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8cdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8cdb-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b8cdb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b8cdb-105">Methods</span></span>  
 <span data-ttu-id="b8cdb-106">Atribut DeliveryRequirementsAttribute Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b8cdb-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b8cdb-107">Properties</span></span>  
 <span data-ttu-id="b8cdb-108">Atribut DeliveryRequirementsAttribute třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b8cdb-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="b8cdb-109">Atribut QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="b8cdb-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="b8cdb-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b8cdb-110">Data type: string</span></span>  
  
 <span data-ttu-id="b8cdb-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b8cdb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8cdb-112">Určuje, zda vazba pro službu podporuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="b8cdb-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="b8cdb-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="b8cdb-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="b8cdb-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="b8cdb-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b8cdb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8cdb-116">Určuje, zda vazba podporuje objednané zprávy.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="b8cdb-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="b8cdb-117">TargetContract</span></span>  
 <span data-ttu-id="b8cdb-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b8cdb-118">Data type: string</span></span>  
  
 <span data-ttu-id="b8cdb-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b8cdb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8cdb-120">Kontrakt, ke kterému se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8cdb-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8cdb-121">Requirements</span></span>  
  
|<span data-ttu-id="b8cdb-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="b8cdb-122">MOF</span></span>|<span data-ttu-id="b8cdb-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b8cdb-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b8cdb-124">Namespace</span></span>|<span data-ttu-id="b8cdb-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b8cdb-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8cdb-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8cdb-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
