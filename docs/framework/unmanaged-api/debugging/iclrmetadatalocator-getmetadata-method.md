---
title: ICLRMetadataLocator::GetMetadata – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 235b93f4176858372a83331730ddea8b97179cc8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738367"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="c56f0-102">ICLRMetadataLocator::GetMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="c56f0-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="c56f0-103">Volá se službami common language runtime (CLR) přístup k datům pro načtení metadat bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="c56f0-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c56f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c56f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c56f0-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="c56f0-106">[in] Řetězec, který určuje cestu k souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c56f0-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="c56f0-107">[in] Časové razítko souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c56f0-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="c56f0-108">[in] Velikost souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="c56f0-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="c56f0-109">[in] Globálně jedinečný identifikátor používaného obrázku.</span><span class="sxs-lookup"><span data-stu-id="c56f0-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="c56f0-110">[in] Relativní virtuální adresu (RVA) metadat.</span><span class="sxs-lookup"><span data-stu-id="c56f0-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="c56f0-111">Adresa je relativní vzhledem k základní adrese image.</span><span class="sxs-lookup"><span data-stu-id="c56f0-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="c56f0-112">[in] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="c56f0-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="c56f0-113">[in] Velikost vyrovnávací paměti, do které se má umístit metadata.</span><span class="sxs-lookup"><span data-stu-id="c56f0-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c56f0-114">[out] Vyrovnávací paměť, ve které chcete umístit metadata.</span><span class="sxs-lookup"><span data-stu-id="c56f0-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="c56f0-115">[out] Velikost metadat, která je vrácena.</span><span class="sxs-lookup"><span data-stu-id="c56f0-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c56f0-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c56f0-116">Remarks</span></span>  
 <span data-ttu-id="c56f0-117">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c56f0-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c56f0-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c56f0-118">Requirements</span></span>  
 <span data-ttu-id="c56f0-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c56f0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c56f0-120">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c56f0-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c56f0-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c56f0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c56f0-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c56f0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56f0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c56f0-123">See also</span></span>

- [<span data-ttu-id="c56f0-124">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c56f0-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
