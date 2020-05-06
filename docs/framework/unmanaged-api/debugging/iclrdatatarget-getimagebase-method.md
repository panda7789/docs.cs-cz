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
ms.openlocfilehash: 71b07e11cd3fec1a0dbebe986d98067c2e6f18e1
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860628"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="0d303-102">ICLRDataTarget::GetImageBase – metoda</span><span class="sxs-lookup"><span data-stu-id="0d303-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="0d303-103">Získá základní adresu paměti určeného obrázku.</span><span class="sxs-lookup"><span data-stu-id="0d303-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d303-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d303-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d303-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d303-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="0d303-106">pro Název souboru obrázku, včetně jeho cesty</span><span class="sxs-lookup"><span data-stu-id="0d303-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="0d303-107">mimo Ukazatel na CLRDATA_ADDRESS, který ukládá základní adresu obrázku.</span><span class="sxs-lookup"><span data-stu-id="0d303-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d303-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d303-108">Remarks</span></span>  
 <span data-ttu-id="0d303-109">Název souboru obrázku může nebo nemusí mít cestu.</span><span class="sxs-lookup"><span data-stu-id="0d303-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="0d303-110">Je-li zadána cesta, je shoda provedena na celé cestě; v opačném případě se shoda provede pouze s názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="0d303-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d303-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d303-111">Requirements</span></span>  
 <span data-ttu-id="0d303-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d303-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d303-113">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0d303-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0d303-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0d303-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d303-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d303-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d303-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d303-116">See also</span></span>

- [<span data-ttu-id="0d303-117">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d303-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
