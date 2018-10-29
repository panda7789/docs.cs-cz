---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194771"
---
# <a name="wsattracerecord"></a><span data-ttu-id="28b33-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="28b33-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="28b33-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="28b33-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28b33-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="28b33-105">Metody</span><span class="sxs-lookup"><span data-stu-id="28b33-105">Methods</span></span>  
 <span data-ttu-id="28b33-106">Třída WSAT_TraceRecord nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="28b33-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="28b33-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="28b33-107">Properties</span></span>  
 <span data-ttu-id="28b33-108">Třída WSAT_TraceRecord má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="28b33-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="28b33-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="28b33-109">ActivityID</span></span>  
 <span data-ttu-id="28b33-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="28b33-110">Data type: object</span></span>  
<span data-ttu-id="28b33-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="28b33-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28b33-112">ID aktivity záznamu trace.</span><span class="sxs-lookup"><span data-stu-id="28b33-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="28b33-113">ID události</span><span class="sxs-lookup"><span data-stu-id="28b33-113">EventID</span></span>  
 <span data-ttu-id="28b33-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="28b33-114">Data type: sint32</span></span>  
<span data-ttu-id="28b33-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="28b33-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28b33-116">ID události trasování záznamu.</span><span class="sxs-lookup"><span data-stu-id="28b33-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="28b33-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="28b33-117">TraceRecord</span></span>  
 <span data-ttu-id="28b33-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="28b33-118">Data type: string</span></span>  
<span data-ttu-id="28b33-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="28b33-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28b33-120">Záznam trasování</span><span class="sxs-lookup"><span data-stu-id="28b33-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28b33-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28b33-121">Requirements</span></span>  
  
|<span data-ttu-id="28b33-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="28b33-122">MOF</span></span>|<span data-ttu-id="28b33-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="28b33-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="28b33-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="28b33-124">Namespace</span></span>|<span data-ttu-id="28b33-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="28b33-125">Defined in root\ServiceModel</span></span>|
