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
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178408"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="2f5f2-102">ICorPublishAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="2f5f2-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="2f5f2-103">Získá název domény aplikace, která je reprezentována touto [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2f5f2-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f5f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f5f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f5f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f5f2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2f5f2-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="2f5f2-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2f5f2-107">[out] Ukazatel na počet širokých znaků, včetně znaku `szName` null, vráceného v poli.</span><span class="sxs-lookup"><span data-stu-id="2f5f2-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="2f5f2-108">[out] Pole, do kterého chcete uložit název.</span><span class="sxs-lookup"><span data-stu-id="2f5f2-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f5f2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f5f2-109">Remarks</span></span>  
 <span data-ttu-id="2f5f2-110">Pokud `szName` je non-null, `GetName` metoda `cchName` zkopíruje až znaky (včetně zakončení null) do `szName`.</span><span class="sxs-lookup"><span data-stu-id="2f5f2-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="2f5f2-111">Pokud je vrácena hodnota `pcchName`non-null , je v `szName` poli uložen skutečný počet znaků v názvu (včetně zakončení null).</span><span class="sxs-lookup"><span data-stu-id="2f5f2-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="2f5f2-112">Metoda `GetName` vrátí S_OK HRESULT bez ohledu na to, kolik znaků bylo zkopírováno.</span><span class="sxs-lookup"><span data-stu-id="2f5f2-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f5f2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f5f2-113">Requirements</span></span>  
 <span data-ttu-id="2f5f2-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f5f2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f5f2-115">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2f5f2-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2f5f2-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f5f2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f5f2-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f5f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5f2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f5f2-118">See also</span></span>

- [<span data-ttu-id="2f5f2-119">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f5f2-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
