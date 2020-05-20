---
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException – metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
ms.openlocfilehash: 969d74933e908674225684a2e77d5c4804b86122
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615641"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="48d3a-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="48d3a-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="48d3a-103">Získá blok programu Watson pro aktuální výjimku v volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="48d3a-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="48d3a-104">*Interval* je kolekce dat o chybách, která souvisí se stejnou chybou kódu.</span><span class="sxs-lookup"><span data-stu-id="48d3a-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="48d3a-105">*Watson* odkazuje na sadu technologií pro shromažďování a analýzu dat, která jsou spojena s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="48d3a-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48d3a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48d3a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48d3a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="48d3a-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="48d3a-108">mimo Ukazatel na strukturu [bucketparameters –](bucketparameters-structure.md) , která obsahuje data o chybách pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="48d3a-108">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48d3a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48d3a-109">Requirements</span></span>  
 <span data-ttu-id="48d3a-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48d3a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48d3a-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="48d3a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48d3a-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48d3a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48d3a-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48d3a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d3a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="48d3a-114">See also</span></span>

- [<span data-ttu-id="48d3a-115">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48d3a-115">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
