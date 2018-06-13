---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 1136647ce668dbb69bdb8acf8ed62343831464b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487773"
---
# <a name="wsattracerecord"></a><span data-ttu-id="cb4ac-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="cb4ac-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="cb4ac-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="cb4ac-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb4ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb4ac-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cb4ac-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cb4ac-105">Methods</span></span>  
 <span data-ttu-id="cb4ac-106">Třída WSAT_TraceRecord nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cb4ac-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cb4ac-107">Properties</span></span>  
 <span data-ttu-id="cb4ac-108">Třída WSAT_TraceRecord má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cb4ac-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="cb4ac-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="cb4ac-109">ActivityID</span></span>  
 <span data-ttu-id="cb4ac-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="cb4ac-110">Data type: object</span></span>  
<span data-ttu-id="cb4ac-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cb4ac-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb4ac-112">ID aktivity záznamu trasování.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="cb4ac-113">ID události</span><span class="sxs-lookup"><span data-stu-id="cb4ac-113">EventID</span></span>  
 <span data-ttu-id="cb4ac-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cb4ac-114">Data type: sint32</span></span>  
<span data-ttu-id="cb4ac-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cb4ac-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb4ac-116">Událost s ID záznamu trasování.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="cb4ac-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="cb4ac-117">TraceRecord</span></span>  
 <span data-ttu-id="cb4ac-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="cb4ac-118">Data type: string</span></span>  
<span data-ttu-id="cb4ac-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cb4ac-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb4ac-120">Záznam trasování</span><span class="sxs-lookup"><span data-stu-id="cb4ac-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb4ac-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb4ac-121">Requirements</span></span>  
  
|<span data-ttu-id="cb4ac-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cb4ac-122">MOF</span></span>|<span data-ttu-id="cb4ac-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cb4ac-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="cb4ac-124">Namespace</span></span>|<span data-ttu-id="cb4ac-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cb4ac-125">Defined in root\ServiceModel</span></span>|
