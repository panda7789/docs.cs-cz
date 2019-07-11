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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 354e1b0dad942534068d5fb07071ed4ac695fb49
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764881"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="c5d41-102">ICorPublishProcess::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="c5d41-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="c5d41-103">Získá úplnou cestu ke spustitelnému souboru pro proces odkazuje toto [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c5d41-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5d41-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5d41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5d41-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c5d41-106">[in] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="c5d41-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c5d41-107">[out] Počet širokých znaků, které jsou vráceny v `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="c5d41-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="c5d41-108">[out] Pole pro uložení názvu, včetně úplné cesty ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="c5d41-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="c5d41-109">Název je zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5d41-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d41-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5d41-110">Requirements</span></span>  
 <span data-ttu-id="c5d41-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d41-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d41-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c5d41-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c5d41-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5d41-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5d41-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d41-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d41-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5d41-115">See also</span></span>

- [<span data-ttu-id="c5d41-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5d41-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
