---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acbc346da940caf933868a03295744132bda4733
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="9662b-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="9662b-102">ActivityTransfer</span></span>
<span data-ttu-id="9662b-103">Událost přenosu aktivity</span><span class="sxs-lookup"><span data-stu-id="9662b-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9662b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9662b-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9662b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9662b-105">Methods</span></span>  
 <span data-ttu-id="9662b-106">Třída ActivityTransfer nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="9662b-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9662b-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9662b-107">Properties</span></span>  
 <span data-ttu-id="9662b-108">Třída ActivityTransfer má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9662b-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="9662b-109">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="9662b-109">ActivityID</span></span>  
  
-   <span data-ttu-id="9662b-110">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="9662b-110">Data type: object</span></span>  
    <span data-ttu-id="9662b-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9662b-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="9662b-112">ID aktivity</span><span class="sxs-lookup"><span data-stu-id="9662b-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="9662b-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="9662b-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="9662b-114">Datový typ: objekt</span><span class="sxs-lookup"><span data-stu-id="9662b-114">Data type: object</span></span>  
    <span data-ttu-id="9662b-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9662b-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="9662b-116">ID související aktivity</span><span class="sxs-lookup"><span data-stu-id="9662b-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9662b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9662b-117">Requirements</span></span>  
  
|<span data-ttu-id="9662b-118">MOF</span><span class="sxs-lookup"><span data-stu-id="9662b-118">MOF</span></span>|<span data-ttu-id="9662b-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9662b-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9662b-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="9662b-120">Namespace</span></span>|<span data-ttu-id="9662b-121">Definované v root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="9662b-121">Defined in root\ServiceModel.</span></span>|
