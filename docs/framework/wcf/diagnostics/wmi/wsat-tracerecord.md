---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923406"
---
# <a name="wsattracerecord"></a><span data-ttu-id="f7d29-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f7d29-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="f7d29-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f7d29-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7d29-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f7d29-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f7d29-105">Methods</span></span>  
 <span data-ttu-id="f7d29-106">Třída WSAT_TraceRecord nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f7d29-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f7d29-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f7d29-107">Properties</span></span>  
 <span data-ttu-id="f7d29-108">Třída WSAT_TraceRecord má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f7d29-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="f7d29-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="f7d29-109">ActivityID</span></span>  
 <span data-ttu-id="f7d29-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="f7d29-110">Data type: object</span></span>  
<span data-ttu-id="f7d29-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f7d29-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f7d29-112">ID aktivity záznamu trace.</span><span class="sxs-lookup"><span data-stu-id="f7d29-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="f7d29-113">ID události</span><span class="sxs-lookup"><span data-stu-id="f7d29-113">EventID</span></span>  
 <span data-ttu-id="f7d29-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f7d29-114">Data type: sint32</span></span>  
<span data-ttu-id="f7d29-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f7d29-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f7d29-116">ID události trasování záznamu.</span><span class="sxs-lookup"><span data-stu-id="f7d29-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="f7d29-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f7d29-117">TraceRecord</span></span>  
 <span data-ttu-id="f7d29-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f7d29-118">Data type: string</span></span>  
<span data-ttu-id="f7d29-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f7d29-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f7d29-120">Záznam trasování</span><span class="sxs-lookup"><span data-stu-id="f7d29-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d29-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7d29-121">Requirements</span></span>  
  
|<span data-ttu-id="f7d29-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="f7d29-122">MOF</span></span>|<span data-ttu-id="f7d29-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f7d29-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f7d29-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f7d29-124">Namespace</span></span>|<span data-ttu-id="f7d29-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f7d29-125">Defined in root\ServiceModel</span></span>|
