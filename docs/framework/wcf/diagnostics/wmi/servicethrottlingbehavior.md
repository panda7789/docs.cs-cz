---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 779aabf5ec9b1bca7151eaf781c6dd6f2631b58f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="b1aea-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="b1aea-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="b1aea-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="b1aea-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1aea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1aea-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b1aea-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b1aea-105">Methods</span></span>  
 <span data-ttu-id="b1aea-106">Třída třídy ServiceThrottlingBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b1aea-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b1aea-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b1aea-107">Properties</span></span>  
 <span data-ttu-id="b1aea-108">Třída třídy ServiceThrottlingBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b1aea-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="b1aea-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="b1aea-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="b1aea-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b1aea-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="b1aea-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b1aea-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1aea-112">Maximální počet zpráv ve všech objektech dispečera v ServiceHost aktivně zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="b1aea-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="b1aea-113">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="b1aea-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="b1aea-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b1aea-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b1aea-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b1aea-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1aea-116">Maximální počet objekty služby, které mohou být prováděny současně.</span><span class="sxs-lookup"><span data-stu-id="b1aea-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="b1aea-117">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="b1aea-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="b1aea-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b1aea-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="b1aea-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b1aea-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1aea-120">Maximální počet relací, které hostitele může přijmout najednou.</span><span class="sxs-lookup"><span data-stu-id="b1aea-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1aea-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1aea-121">Requirements</span></span>  
  
|<span data-ttu-id="b1aea-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b1aea-122">MOF</span></span>|<span data-ttu-id="b1aea-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b1aea-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b1aea-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b1aea-124">Namespace</span></span>|<span data-ttu-id="b1aea-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b1aea-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1aea-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1aea-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
