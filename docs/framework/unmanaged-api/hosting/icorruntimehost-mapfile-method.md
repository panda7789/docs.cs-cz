---
title: ICorRuntimeHost::MapFile – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 956de98fca1caec0ac1b94afc7251f9741246f94
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494776"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="b8c0d-102">ICorRuntimeHost::MapFile – metoda</span><span class="sxs-lookup"><span data-stu-id="b8c0d-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="b8c0d-103">Mapuje zadaný soubor do paměti.</span><span class="sxs-lookup"><span data-stu-id="b8c0d-103">Maps the specified file into memory.</span></span> <span data-ttu-id="b8c0d-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b8c0d-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c0d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8c0d-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8c0d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8c0d-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="b8c0d-107">[in] Popisovač souboru, který má být namapována.</span><span class="sxs-lookup"><span data-stu-id="b8c0d-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="b8c0d-108">[out] Počáteční adresa paměti na kterém má být mapování souboru.</span><span class="sxs-lookup"><span data-stu-id="b8c0d-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c0d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8c0d-109">Requirements</span></span>  
 <span data-ttu-id="b8c0d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c0d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c0d-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b8c0d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8c0d-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8c0d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8c0d-113">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b8c0d-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c0d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8c0d-114">See also</span></span>
- [<span data-ttu-id="b8c0d-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8c0d-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
