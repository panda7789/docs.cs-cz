---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484185"
---
# <a name="activitytransfer"></a><span data-ttu-id="a2151-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="a2151-102">ActivityTransfer</span></span>
<span data-ttu-id="a2151-103">Událost přenosu aktivity</span><span class="sxs-lookup"><span data-stu-id="a2151-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2151-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2151-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a2151-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a2151-105">Methods</span></span>  
 <span data-ttu-id="a2151-106">Třída ActivityTransfer nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a2151-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a2151-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a2151-107">Properties</span></span>  
 <span data-ttu-id="a2151-108">Třída ActivityTransfer má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a2151-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="a2151-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="a2151-109">ActivityID</span></span>  
  
-   <span data-ttu-id="a2151-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="a2151-110">Data type: object</span></span>  
    <span data-ttu-id="a2151-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a2151-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="a2151-112">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="a2151-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="a2151-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="a2151-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="a2151-114">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="a2151-114">Data type: object</span></span>  
    <span data-ttu-id="a2151-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a2151-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="a2151-116">ID související aktivity</span><span class="sxs-lookup"><span data-stu-id="a2151-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2151-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2151-117">Requirements</span></span>  
  
|<span data-ttu-id="a2151-118">MOF</span><span class="sxs-lookup"><span data-stu-id="a2151-118">MOF</span></span>|<span data-ttu-id="a2151-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a2151-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a2151-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a2151-120">Namespace</span></span>|<span data-ttu-id="a2151-121">Definované v root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="a2151-121">Defined in root\ServiceModel.</span></span>|
