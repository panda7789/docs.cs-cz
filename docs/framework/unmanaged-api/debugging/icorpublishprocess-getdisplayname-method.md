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
ms.openlocfilehash: 815f2e2f695837c973210a21ab3631ef307c23d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423634"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="b9800-102">ICorPublishProcess::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="b9800-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="b9800-103">Získá úplnou cestu ke spustitelnému souboru procesu, který odkazuje toto [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b9800-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9800-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9800-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9800-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9800-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b9800-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="b9800-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b9800-107">[out] Číslo, vrátí se v široké znaky `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="b9800-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="b9800-108">[out] Pole k uložení názvu, včetně úplná cesta ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="b9800-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="b9800-109">Název je ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b9800-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9800-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9800-110">Requirements</span></span>  
 <span data-ttu-id="b9800-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9800-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9800-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b9800-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b9800-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9800-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9800-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9800-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9800-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9800-115">See Also</span></span>  
 [<span data-ttu-id="b9800-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9800-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
