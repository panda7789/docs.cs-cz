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
ms.openlocfilehash: 9dbb655d6ed0b9bd88c5eedf61a191401a805fb3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738754"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="dcba3-102">ICLRDataTarget::GetImageBase – metoda</span><span class="sxs-lookup"><span data-stu-id="dcba3-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="dcba3-103">Získá adresu základní paměti zadané bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="dcba3-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcba3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcba3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcba3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcba3-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="dcba3-106">[in] Název souboru obrázku, včetně jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="dcba3-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="dcba3-107">[out] Ukazatel na CLRDATA_ADDRESS, která ukládá adresu základní Image.</span><span class="sxs-lookup"><span data-stu-id="dcba3-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcba3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcba3-108">Remarks</span></span>  
 <span data-ttu-id="dcba3-109">Název souboru obrázku může nebo nemusí mít cestu.</span><span class="sxs-lookup"><span data-stu-id="dcba3-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="dcba3-110">Pokud je zadána cesta, odpovídající se provádí na celou cestu. v opačném případě odpovídající se provádí pouze na název souboru.</span><span class="sxs-lookup"><span data-stu-id="dcba3-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcba3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcba3-111">Requirements</span></span>  
 <span data-ttu-id="dcba3-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcba3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcba3-113">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="dcba3-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dcba3-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcba3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcba3-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcba3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcba3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcba3-116">See also</span></span>

- [<span data-ttu-id="dcba3-117">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcba3-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
