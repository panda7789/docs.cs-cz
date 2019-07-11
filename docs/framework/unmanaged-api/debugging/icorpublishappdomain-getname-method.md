---
title: ICorPublishAppDomain::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b518a3be939c70b207a71d79a3d362dba26fd3d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774199"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="4a3a0-102">ICorPublishAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="4a3a0-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="4a3a0-103">Získá název domény aplikace, která je reprezentována to [icorpublishappdomain –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4a3a0-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a3a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a3a0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a3a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a3a0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="4a3a0-106">[in] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="4a3a0-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4a3a0-107">[out] Ukazatel na počet širokých znaků, včetně znaku null, vrátí v `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="4a3a0-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="4a3a0-108">[out] Pole pro uložení názvu.</span><span class="sxs-lookup"><span data-stu-id="4a3a0-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a3a0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a3a0-109">Remarks</span></span>  
 <span data-ttu-id="4a3a0-110">Pokud `szName` je jiná než null, `GetName` metoda zkopíruje až `cchName` znaků (včetně ukončovacího znaku null) do `szName`.</span><span class="sxs-lookup"><span data-stu-id="4a3a0-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="4a3a0-111">Pokud se vrátí jinou hodnotu null v `pcchName`, skutečný počet znaků v názvu (včetně ukončovacího znaku null) je uložen v `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="4a3a0-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="4a3a0-112">`GetName` Metoda vrátí hodnotu S_OK HRESULT bez ohledu na to, kolik znaků byly zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="4a3a0-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a3a0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a3a0-113">Requirements</span></span>  
 <span data-ttu-id="4a3a0-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a3a0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a3a0-115">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="4a3a0-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4a3a0-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a3a0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a3a0-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a3a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3a0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a3a0-118">See also</span></span>

- [<span data-ttu-id="4a3a0-119">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a3a0-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
