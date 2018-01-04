---
title: "ICorRuntimeHost::MapFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.MapFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3047a473f36762ec57ae4ea87067e941ac568c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="f0f03-102">ICorRuntimeHost::MapFile – metoda</span><span class="sxs-lookup"><span data-stu-id="f0f03-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="f0f03-103">Mapuje zadaný soubor do paměti.</span><span class="sxs-lookup"><span data-stu-id="f0f03-103">Maps the specified file into memory.</span></span> <span data-ttu-id="f0f03-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f0f03-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f03-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0f03-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0f03-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0f03-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="f0f03-107">[v] Popisovač souboru, který se namapovat.</span><span class="sxs-lookup"><span data-stu-id="f0f03-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="f0f03-108">[out] Počáteční adresa paměti, kdy má začít mapování souboru.</span><span class="sxs-lookup"><span data-stu-id="f0f03-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0f03-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0f03-109">Requirements</span></span>  
 <span data-ttu-id="f0f03-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0f03-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0f03-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0f03-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0f03-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0f03-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0f03-113">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="f0f03-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f03-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0f03-114">See Also</span></span>  
 [<span data-ttu-id="f0f03-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0f03-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
