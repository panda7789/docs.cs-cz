---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964291"
---
# <a name="activitytransfer"></a><span data-ttu-id="f2315-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="f2315-102">ActivityTransfer</span></span>
<span data-ttu-id="f2315-103">Aktivita událost přenosu</span><span class="sxs-lookup"><span data-stu-id="f2315-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2315-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2315-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f2315-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f2315-105">Methods</span></span>  
 <span data-ttu-id="f2315-106">Třída ActivityTransfer nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f2315-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f2315-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2315-107">Properties</span></span>  
 <span data-ttu-id="f2315-108">Třída ActivityTransfer má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f2315-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="f2315-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="f2315-109">ActivityID</span></span>  
  
- <span data-ttu-id="f2315-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="f2315-110">Data type: object</span></span>  
    <span data-ttu-id="f2315-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2315-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="f2315-112">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="f2315-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="f2315-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="f2315-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="f2315-114">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="f2315-114">Data type: object</span></span>  
    <span data-ttu-id="f2315-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2315-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="f2315-116">ID související aktivity</span><span class="sxs-lookup"><span data-stu-id="f2315-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2315-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2315-117">Requirements</span></span>  
  
|<span data-ttu-id="f2315-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="f2315-118">MOF</span></span>|<span data-ttu-id="f2315-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f2315-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f2315-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f2315-120">Namespace</span></span>|<span data-ttu-id="f2315-121">Definované v root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="f2315-121">Defined in root\ServiceModel.</span></span>|
