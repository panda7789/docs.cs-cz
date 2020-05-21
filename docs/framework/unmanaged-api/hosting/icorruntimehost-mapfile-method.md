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
ms.openlocfilehash: 3b1a0cd9a1dfba6f33a20416f2a10c967f871a06
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762666"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="4df46-102">ICorRuntimeHost::MapFile – metoda</span><span class="sxs-lookup"><span data-stu-id="4df46-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="4df46-103">Namapuje zadaný soubor na paměť.</span><span class="sxs-lookup"><span data-stu-id="4df46-103">Maps the specified file into memory.</span></span> <span data-ttu-id="4df46-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="4df46-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df46-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4df46-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4df46-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4df46-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="4df46-107">pro Popisovač souboru, který má být namapován.</span><span class="sxs-lookup"><span data-stu-id="4df46-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="4df46-108">mimo Počáteční adresa paměti, na které chcete zahájit mapování souboru.</span><span class="sxs-lookup"><span data-stu-id="4df46-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df46-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4df46-109">Requirements</span></span>  
 <span data-ttu-id="4df46-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4df46-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df46-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4df46-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4df46-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4df46-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4df46-113">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="4df46-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df46-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4df46-114">See also</span></span>

- [<span data-ttu-id="4df46-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4df46-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
