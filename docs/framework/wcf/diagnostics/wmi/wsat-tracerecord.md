---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="9adbd-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="9adbd-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="9adbd-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="9adbd-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9adbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9adbd-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9adbd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9adbd-105">Methods</span></span>  
 <span data-ttu-id="9adbd-106">Třída WSAT_TraceRecord nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="9adbd-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9adbd-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9adbd-107">Properties</span></span>  
 <span data-ttu-id="9adbd-108">Třída WSAT_TraceRecord má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9adbd-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="9adbd-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="9adbd-109">ActivityID</span></span>  
 <span data-ttu-id="9adbd-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="9adbd-110">Data type: object</span></span>  
<span data-ttu-id="9adbd-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9adbd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9adbd-112">ID aktivity záznamu trasování.</span><span class="sxs-lookup"><span data-stu-id="9adbd-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="9adbd-113">ID události</span><span class="sxs-lookup"><span data-stu-id="9adbd-113">EventID</span></span>  
 <span data-ttu-id="9adbd-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="9adbd-114">Data type: sint32</span></span>  
<span data-ttu-id="9adbd-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9adbd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9adbd-116">Událost s ID záznamu trasování.</span><span class="sxs-lookup"><span data-stu-id="9adbd-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="9adbd-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="9adbd-117">TraceRecord</span></span>  
 <span data-ttu-id="9adbd-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="9adbd-118">Data type: string</span></span>  
<span data-ttu-id="9adbd-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9adbd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9adbd-120">Záznam trasování</span><span class="sxs-lookup"><span data-stu-id="9adbd-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9adbd-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9adbd-121">Requirements</span></span>  
  
|<span data-ttu-id="9adbd-122">MOF</span><span class="sxs-lookup"><span data-stu-id="9adbd-122">MOF</span></span>|<span data-ttu-id="9adbd-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9adbd-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9adbd-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="9adbd-124">Namespace</span></span>|<span data-ttu-id="9adbd-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9adbd-125">Defined in root\ServiceModel</span></span>|
