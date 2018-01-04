---
title: "ICLRDataTarget::GetImageBase – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetImageBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 504c3ce7115cbab11d0510eaa2ebb0fdd9f1888b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="7da3f-102">ICLRDataTarget::GetImageBase – metoda</span><span class="sxs-lookup"><span data-stu-id="7da3f-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="7da3f-103">Získá základní paměti adresu zadanou bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="7da3f-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7da3f-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7da3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7da3f-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="7da3f-106">[v] Název souboru obrázku, včetně jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="7da3f-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="7da3f-107">[out] Ukazatel na CLRDATA_ADDRESS, uchovávající základní adresu bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="7da3f-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7da3f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7da3f-108">Remarks</span></span>  
 <span data-ttu-id="7da3f-109">Název souboru obrázku může nebo nemusí mít cestu.</span><span class="sxs-lookup"><span data-stu-id="7da3f-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="7da3f-110">Pokud je cesta zadána, odpovídající se provádí na celou cestu. v ostatních případech porovnávání se provádí pouze na název souboru.</span><span class="sxs-lookup"><span data-stu-id="7da3f-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7da3f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7da3f-111">Requirements</span></span>  
 <span data-ttu-id="7da3f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7da3f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7da3f-113">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="7da3f-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7da3f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7da3f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7da3f-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7da3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da3f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7da3f-116">See Also</span></span>  
 [<span data-ttu-id="7da3f-117">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7da3f-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
