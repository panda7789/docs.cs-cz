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
ms.openlocfilehash: 7f2e644340a2ec7fe807830422b927ce811ddcf9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790565"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="a25f5-102">ICorPublishProcess::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="a25f5-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="a25f5-103">Získá úplnou cestu ke spustitelnému souboru pro proces, na který odkazuje tento [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a25f5-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a25f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a25f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a25f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a25f5-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a25f5-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="a25f5-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a25f5-107">mimo Počet velkých znaků vrácených v poli `szName`.</span><span class="sxs-lookup"><span data-stu-id="a25f5-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="a25f5-108">mimo Pole, do kterého se má uložit název, včetně úplné cesty spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="a25f5-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="a25f5-109">Název je zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a25f5-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a25f5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a25f5-110">Requirements</span></span>  
 <span data-ttu-id="a25f5-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a25f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a25f5-112">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a25f5-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a25f5-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a25f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a25f5-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a25f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25f5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a25f5-115">See also</span></span>

- [<span data-ttu-id="a25f5-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a25f5-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
