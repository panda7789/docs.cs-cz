---
title: ICorPublishProcess::GetDisplayName – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
ms.openlocfilehash: df2750f082ddc40bbeee121116c3e877d037da84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140427"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="77e20-102">ICorPublishProcess::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="77e20-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="77e20-103">Získá úplnou cestu ke spustitelnému souboru pro proces, na který odkazuje tento [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="77e20-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77e20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77e20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77e20-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="77e20-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="77e20-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="77e20-107">mimo Počet velkých znaků vrácených v poli `szName`.</span><span class="sxs-lookup"><span data-stu-id="77e20-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="77e20-108">mimo Pole, do kterého se má uložit název, včetně úplné cesty spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="77e20-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="77e20-109">Název je zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="77e20-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e20-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77e20-110">Requirements</span></span>  
 <span data-ttu-id="77e20-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e20-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e20-112">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="77e20-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="77e20-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="77e20-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77e20-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e20-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e20-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77e20-115">See also</span></span>

- [<span data-ttu-id="77e20-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77e20-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
