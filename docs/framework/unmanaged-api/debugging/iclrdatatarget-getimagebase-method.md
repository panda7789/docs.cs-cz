---
title: ICLRDataTarget::GetImageBase – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
ms.openlocfilehash: fed643ae52f50b1b8cd134880c644c8941da6f56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122878"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="7b018-102">ICLRDataTarget::GetImageBase – metoda</span><span class="sxs-lookup"><span data-stu-id="7b018-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="7b018-103">Získá základní adresu paměti určeného obrázku.</span><span class="sxs-lookup"><span data-stu-id="7b018-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b018-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b018-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b018-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b018-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="7b018-106">pro Název souboru obrázku, včetně jeho cesty</span><span class="sxs-lookup"><span data-stu-id="7b018-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="7b018-107">mimo Ukazatel na CLRDATA_ADDRESS, který ukládá základní adresu obrázku.</span><span class="sxs-lookup"><span data-stu-id="7b018-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b018-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b018-108">Remarks</span></span>  
 <span data-ttu-id="7b018-109">Název souboru obrázku může nebo nemusí mít cestu.</span><span class="sxs-lookup"><span data-stu-id="7b018-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="7b018-110">Je-li zadána cesta, je shoda provedena na celé cestě; v opačném případě se shoda provede pouze s názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="7b018-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b018-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b018-111">Requirements</span></span>  
 <span data-ttu-id="7b018-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b018-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b018-113">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7b018-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7b018-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7b018-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b018-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b018-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b018-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b018-116">See also</span></span>

- [<span data-ttu-id="7b018-117">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b018-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
