---
title: "ICorPublishProcess::GetDisplayName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetDisplayName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98c751b29f1bffd8baa8b87548d588c6db98eed2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="63b98-102">ICorPublishProcess::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="63b98-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="63b98-103">Získá úplnou cestu ke spustitelnému souboru procesu, který odkazuje toto [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="63b98-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63b98-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63b98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63b98-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="63b98-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="63b98-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="63b98-107">[out] Číslo, vrátí se v široké znaky `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="63b98-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="63b98-108">[out] Pole k uložení názvu, včetně úplná cesta ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="63b98-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="63b98-109">Název je ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="63b98-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63b98-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63b98-110">Requirements</span></span>  
 <span data-ttu-id="63b98-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63b98-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63b98-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="63b98-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="63b98-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63b98-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63b98-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63b98-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b98-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="63b98-115">See Also</span></span>  
 [<span data-ttu-id="63b98-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63b98-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
