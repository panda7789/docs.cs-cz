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
ms.openlocfilehash: 814073b766d5d562b414a566ae3f92abd664ce35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707840"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="b1b77-102">ICorRuntimeHost::MapFile – metoda</span><span class="sxs-lookup"><span data-stu-id="b1b77-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="b1b77-103">Mapuje zadaný soubor do paměti.</span><span class="sxs-lookup"><span data-stu-id="b1b77-103">Maps the specified file into memory.</span></span> <span data-ttu-id="b1b77-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b1b77-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b77-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1b77-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1b77-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1b77-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="b1b77-107">[in] Popisovač souboru, který má být namapována.</span><span class="sxs-lookup"><span data-stu-id="b1b77-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="b1b77-108">[out] Počáteční adresa paměti na kterém má být mapování souboru.</span><span class="sxs-lookup"><span data-stu-id="b1b77-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1b77-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1b77-109">Requirements</span></span>  
 <span data-ttu-id="b1b77-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1b77-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b77-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1b77-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1b77-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1b77-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1b77-113">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b1b77-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b77-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1b77-114">See also</span></span>
- [<span data-ttu-id="b1b77-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1b77-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
