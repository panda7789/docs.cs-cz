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
ms.openlocfilehash: 4325d61d12a66b17f88e5e368cbbc7806d0a3ec5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790709"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="c95ec-102">ICorPublishAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="c95ec-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="c95ec-103">Získá název domény aplikace, která je reprezentovaná tímto [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c95ec-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c95ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c95ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c95ec-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c95ec-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="c95ec-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c95ec-107">mimo Ukazatel na počet velkých znaků, včetně znaku null, vrácený v poli `szName`.</span><span class="sxs-lookup"><span data-stu-id="c95ec-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="c95ec-108">mimo Pole, do kterého se má uložit název</span><span class="sxs-lookup"><span data-stu-id="c95ec-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c95ec-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c95ec-109">Remarks</span></span>  
 <span data-ttu-id="c95ec-110">Pokud `szName` není null, metoda `GetName` kopíruje až `cchName` znaky (včetně ukončovacího znaku null) do `szName`.</span><span class="sxs-lookup"><span data-stu-id="c95ec-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="c95ec-111">Pokud je v `pcchName`vrácena hodnota, která není null, je v poli `szName` uložen skutečný počet znaků v názvu (včetně ukončovacího znaku null).</span><span class="sxs-lookup"><span data-stu-id="c95ec-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="c95ec-112">Metoda `GetName` vrátí S_OK HRESULT bez ohledu na to, kolik znaků bylo kopírováno.</span><span class="sxs-lookup"><span data-stu-id="c95ec-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c95ec-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c95ec-113">Requirements</span></span>  
 <span data-ttu-id="c95ec-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c95ec-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c95ec-115">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c95ec-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c95ec-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c95ec-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c95ec-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c95ec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95ec-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c95ec-118">See also</span></span>

- [<span data-ttu-id="c95ec-119">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c95ec-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
