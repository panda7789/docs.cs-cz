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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="a59cc-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="a59cc-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="a59cc-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="a59cc-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a59cc-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a59cc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a59cc-105">Methods</span></span>  
 <span data-ttu-id="a59cc-106">Třída WSAT_TraceRecord nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a59cc-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a59cc-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a59cc-107">Properties</span></span>  
 <span data-ttu-id="a59cc-108">Třída WSAT_TraceRecord má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a59cc-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="a59cc-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="a59cc-109">ActivityID</span></span>  
 <span data-ttu-id="a59cc-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="a59cc-110">Data type: object</span></span>  
<span data-ttu-id="a59cc-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a59cc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a59cc-112">ID aktivity záznamu trasování.</span><span class="sxs-lookup"><span data-stu-id="a59cc-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="a59cc-113">ID události</span><span class="sxs-lookup"><span data-stu-id="a59cc-113">EventID</span></span>  
 <span data-ttu-id="a59cc-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="a59cc-114">Data type: sint32</span></span>  
<span data-ttu-id="a59cc-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a59cc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a59cc-116">Událost s ID záznamu trasování.</span><span class="sxs-lookup"><span data-stu-id="a59cc-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="a59cc-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="a59cc-117">TraceRecord</span></span>  
 <span data-ttu-id="a59cc-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a59cc-118">Data type: string</span></span>  
<span data-ttu-id="a59cc-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a59cc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a59cc-120">Záznam trasování</span><span class="sxs-lookup"><span data-stu-id="a59cc-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59cc-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a59cc-121">Requirements</span></span>  
  
|<span data-ttu-id="a59cc-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a59cc-122">MOF</span></span>|<span data-ttu-id="a59cc-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a59cc-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a59cc-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a59cc-124">Namespace</span></span>|<span data-ttu-id="a59cc-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a59cc-125">Defined in root\ServiceModel</span></span>|
