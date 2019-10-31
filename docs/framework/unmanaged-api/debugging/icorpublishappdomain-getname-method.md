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
ms.openlocfilehash: 2f91891164f1f80617cab10347eb4a7a08762c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140349"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="b3085-102">ICorPublishAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b3085-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="b3085-103">Získá název domény aplikace, která je reprezentovaná tímto [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b3085-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3085-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3085-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3085-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3085-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b3085-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="b3085-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b3085-107">mimo Ukazatel na počet velkých znaků, včetně znaku null, vrácený v poli `szName`.</span><span class="sxs-lookup"><span data-stu-id="b3085-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="b3085-108">mimo Pole, do kterého se má uložit název</span><span class="sxs-lookup"><span data-stu-id="b3085-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3085-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3085-109">Remarks</span></span>  
 <span data-ttu-id="b3085-110">Pokud `szName` není null, metoda `GetName` kopíruje až `cchName` znaky (včetně ukončovacího znaku null) do `szName`.</span><span class="sxs-lookup"><span data-stu-id="b3085-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="b3085-111">Pokud je v `pcchName`vrácena hodnota, která není null, je v poli `szName` uložen skutečný počet znaků v názvu (včetně ukončovacího znaku null).</span><span class="sxs-lookup"><span data-stu-id="b3085-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="b3085-112">Metoda `GetName` vrátí hodnotu S_OK HRESULT bez ohledu na to, kolik znaků bylo kopírováno.</span><span class="sxs-lookup"><span data-stu-id="b3085-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3085-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3085-113">Requirements</span></span>  
 <span data-ttu-id="b3085-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3085-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3085-115">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b3085-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b3085-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b3085-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3085-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3085-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3085-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3085-118">See also</span></span>

- [<span data-ttu-id="b3085-119">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3085-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
