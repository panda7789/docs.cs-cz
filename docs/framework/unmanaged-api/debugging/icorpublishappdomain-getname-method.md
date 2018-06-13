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
ms.openlocfilehash: 796f8ea42cc5cbe13729f7b92e15bc214d62734d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423855"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="a229d-102">ICorPublishAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="a229d-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="a229d-103">Získá název domény aplikace, která je reprezentována to [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a229d-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a229d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a229d-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a229d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a229d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a229d-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="a229d-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a229d-107">[out] Ukazatel na počet široké znaky, včetně znak hodnoty null, vrátí se v `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="a229d-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="a229d-108">[out] Pole, do které chcete uložit název.</span><span class="sxs-lookup"><span data-stu-id="a229d-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a229d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a229d-109">Remarks</span></span>  
 <span data-ttu-id="a229d-110">Pokud `szName` hodnotu Null, `GetName` metoda zkopíruje až `cchName` znaků (včetně null ukončovací znak) do `szName`.</span><span class="sxs-lookup"><span data-stu-id="a229d-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="a229d-111">Pokud se vrátí hodnotu null v `pcchName`, skutečný počet znaků v názvu (včetně null ukončovací znak) je uložen v `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="a229d-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="a229d-112">`GetName` Metoda vrátí HRESULT S_OK bez ohledu na to, kolik znaků byly zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="a229d-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a229d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a229d-113">Requirements</span></span>  
 <span data-ttu-id="a229d-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a229d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a229d-115">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="a229d-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a229d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a229d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a229d-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a229d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a229d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a229d-118">See Also</span></span>  
 [<span data-ttu-id="a229d-119">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a229d-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
