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
ms.openlocfilehash: 4338619414c9c9ac8c5fe85479562410d1678698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403855"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="0c459-102">ICLRMetadataLocator::GetMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="0c459-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="0c459-103">Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup pro načtení metadat bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="0c459-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c459-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c459-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="0c459-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c459-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="0c459-106">[v] Řetězec, který určuje cestu k souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="0c459-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="0c459-107">[v] Časové razítko souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="0c459-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="0c459-108">[v] Velikost souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="0c459-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="0c459-109">[v] Globálně jedinečný identifikátor bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="0c459-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="0c459-110">[v] Relativní virtuální adresy (RVA) metadata.</span><span class="sxs-lookup"><span data-stu-id="0c459-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="0c459-111">Adresa je relativní vzhledem k základní adresu bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="0c459-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="0c459-112">[v] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="0c459-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="0c459-113">[v] Velikost vyrovnávací paměti, do níž umístíte metadata.</span><span class="sxs-lookup"><span data-stu-id="0c459-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0c459-114">[out] Vyrovnávací paměť, do níž umístíte metadata.</span><span class="sxs-lookup"><span data-stu-id="0c459-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="0c459-115">[out] Velikost metadat, která je vrácena.</span><span class="sxs-lookup"><span data-stu-id="0c459-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c459-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c459-116">Remarks</span></span>  
 <span data-ttu-id="0c459-117">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c459-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c459-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c459-118">Requirements</span></span>  
 <span data-ttu-id="0c459-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c459-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c459-120">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0c459-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0c459-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c459-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c459-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c459-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c459-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c459-123">See Also</span></span>  
 [<span data-ttu-id="0c459-124">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c459-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
