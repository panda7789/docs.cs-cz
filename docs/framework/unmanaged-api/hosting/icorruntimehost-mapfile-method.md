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
ms.openlocfilehash: bcf1b49f0576f5dbd73c001f8edff7a9ab29af22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139520"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="fc310-102">ICorRuntimeHost::MapFile – metoda</span><span class="sxs-lookup"><span data-stu-id="fc310-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="fc310-103">Namapuje zadaný soubor na paměť.</span><span class="sxs-lookup"><span data-stu-id="fc310-103">Maps the specified file into memory.</span></span> <span data-ttu-id="fc310-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="fc310-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc310-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc310-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc310-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc310-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="fc310-107">pro Popisovač souboru, který má být namapován.</span><span class="sxs-lookup"><span data-stu-id="fc310-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="fc310-108">mimo Počáteční adresa paměti, na které chcete zahájit mapování souboru.</span><span class="sxs-lookup"><span data-stu-id="fc310-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc310-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc310-109">Requirements</span></span>  
 <span data-ttu-id="fc310-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc310-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc310-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc310-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc310-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc310-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc310-113">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="fc310-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc310-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc310-114">See also</span></span>

- [<span data-ttu-id="fc310-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc310-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
