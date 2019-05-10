---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 6237d65d6964a4ebca34af895158c83239641593
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662813"
---
# <a name="activitytransfer"></a><span data-ttu-id="88fd3-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="88fd3-102">ActivityTransfer</span></span>
<span data-ttu-id="88fd3-103">Aktivita událost přenosu</span><span class="sxs-lookup"><span data-stu-id="88fd3-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88fd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88fd3-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="88fd3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="88fd3-105">Methods</span></span>  
 <span data-ttu-id="88fd3-106">Třída ActivityTransfer nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="88fd3-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="88fd3-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="88fd3-107">Properties</span></span>  
 <span data-ttu-id="88fd3-108">Třída ActivityTransfer má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="88fd3-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="88fd3-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="88fd3-109">ActivityID</span></span>  
  
- <span data-ttu-id="88fd3-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="88fd3-110">Data type: object</span></span>  
    <span data-ttu-id="88fd3-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88fd3-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="88fd3-112">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="88fd3-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="88fd3-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="88fd3-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="88fd3-114">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="88fd3-114">Data type: object</span></span>  
    <span data-ttu-id="88fd3-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88fd3-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="88fd3-116">ID související aktivity</span><span class="sxs-lookup"><span data-stu-id="88fd3-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88fd3-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88fd3-117">Requirements</span></span>  
  
|<span data-ttu-id="88fd3-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="88fd3-118">MOF</span></span>|<span data-ttu-id="88fd3-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="88fd3-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="88fd3-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="88fd3-120">Namespace</span></span>|<span data-ttu-id="88fd3-121">Definované v root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="88fd3-121">Defined in root\ServiceModel.</span></span>|
