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
ms.openlocfilehash: b24f8ed4f5e2c6e0022f5599f2ab8c44a30a561a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129280"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="4bd4f-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="4bd4f-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="4bd4f-103">Získá blok programu Watson pro aktuální výjimku v volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="4bd4f-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="4bd4f-104">*Interval* je kolekce dat o chybách, která souvisí se stejnou chybou kódu.</span><span class="sxs-lookup"><span data-stu-id="4bd4f-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="4bd4f-105">*Watson* odkazuje na sadu technologií pro shromažďování a analýzu dat, která jsou spojena s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="4bd4f-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd4f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bd4f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bd4f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bd4f-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="4bd4f-108">mimo Ukazatel na strukturu [bucketparameters –](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) , která obsahuje data o chybách pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="4bd4f-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bd4f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4bd4f-109">Requirements</span></span>  
 <span data-ttu-id="4bd4f-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bd4f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bd4f-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4bd4f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bd4f-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4bd4f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bd4f-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bd4f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd4f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bd4f-114">See also</span></span>

- [<span data-ttu-id="4bd4f-115">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4bd4f-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
