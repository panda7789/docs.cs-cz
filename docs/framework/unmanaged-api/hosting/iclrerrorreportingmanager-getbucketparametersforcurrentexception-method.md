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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec7e303e5145e16f4c17074d557410ffe4521c20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549834"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="1cec4-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="1cec4-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="1cec4-103">Získá Watson kbelíku pro aktuální výjimky na volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="1cec4-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="1cec4-104">A *kbelíku* je kolekce data chyby týkající se stejnou chybu v kódu.</span><span class="sxs-lookup"><span data-stu-id="1cec4-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="1cec4-105">*Watson* odkazuje na sadu technologií pro shromažďování a analýza dat, který je spojen s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="1cec4-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cec4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cec4-106">Syntax</span></span>  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cec4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cec4-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="1cec4-108">[out] Ukazatel [bucketparameters –](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) strukturu, která obsahuje data o chybách pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="1cec4-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cec4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1cec4-109">Requirements</span></span>  
 <span data-ttu-id="1cec4-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cec4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cec4-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1cec4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1cec4-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1cec4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cec4-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cec4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cec4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1cec4-114">See also</span></span>
- [<span data-ttu-id="1cec4-115">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1cec4-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
