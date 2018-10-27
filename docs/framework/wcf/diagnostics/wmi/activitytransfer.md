---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034419"
---
# <a name="activitytransfer"></a><span data-ttu-id="6dbbd-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="6dbbd-102">ActivityTransfer</span></span>
<span data-ttu-id="6dbbd-103">Aktivita událost přenosu</span><span class="sxs-lookup"><span data-stu-id="6dbbd-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dbbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dbbd-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6dbbd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6dbbd-105">Methods</span></span>  
 <span data-ttu-id="6dbbd-106">Třída ActivityTransfer nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="6dbbd-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6dbbd-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6dbbd-107">Properties</span></span>  
 <span data-ttu-id="6dbbd-108">Třída ActivityTransfer má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="6dbbd-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="6dbbd-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="6dbbd-109">ActivityID</span></span>  
  
-   <span data-ttu-id="6dbbd-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="6dbbd-110">Data type: object</span></span>  
    <span data-ttu-id="6dbbd-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6dbbd-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="6dbbd-112">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="6dbbd-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="6dbbd-113">Mít</span><span class="sxs-lookup"><span data-stu-id="6dbbd-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="6dbbd-114">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="6dbbd-114">Data type: object</span></span>  
    <span data-ttu-id="6dbbd-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6dbbd-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="6dbbd-116">ID související aktivity</span><span class="sxs-lookup"><span data-stu-id="6dbbd-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dbbd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6dbbd-117">Requirements</span></span>  
  
|<span data-ttu-id="6dbbd-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="6dbbd-118">MOF</span></span>|<span data-ttu-id="6dbbd-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6dbbd-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6dbbd-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="6dbbd-120">Namespace</span></span>|<span data-ttu-id="6dbbd-121">Definované v root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="6dbbd-121">Defined in root\ServiceModel.</span></span>|
