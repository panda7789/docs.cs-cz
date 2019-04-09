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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e823911280f52e16c745c9c77fe17b49bd35dc0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129828"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="c9f80-102">ICLRDataTarget::GetImageBase – metoda</span><span class="sxs-lookup"><span data-stu-id="c9f80-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="c9f80-103">Získá adresu základní paměti zadané bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c9f80-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9f80-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9f80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9f80-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="c9f80-106">[in] Název souboru obrázku, včetně jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="c9f80-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="c9f80-107">[out] Ukazatel na CLRDATA_ADDRESS, která ukládá adresu základní Image.</span><span class="sxs-lookup"><span data-stu-id="c9f80-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9f80-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9f80-108">Remarks</span></span>  
 <span data-ttu-id="c9f80-109">Název souboru obrázku může nebo nemusí mít cestu.</span><span class="sxs-lookup"><span data-stu-id="c9f80-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="c9f80-110">Pokud je zadána cesta, odpovídající se provádí na celou cestu. v opačném případě odpovídající se provádí pouze na název souboru.</span><span class="sxs-lookup"><span data-stu-id="c9f80-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f80-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9f80-111">Requirements</span></span>  
 <span data-ttu-id="c9f80-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9f80-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f80-113">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c9f80-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c9f80-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9f80-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c9f80-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c9f80-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c9f80-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9f80-116">See also</span></span>

- [<span data-ttu-id="c9f80-117">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9f80-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
