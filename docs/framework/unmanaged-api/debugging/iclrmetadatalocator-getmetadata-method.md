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
ms.openlocfilehash: 66b3934d000b4f000c368acb1f57c8fc82a5c453
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793628"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="c03d4-102">ICLRMetadataLocator::GetMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="c03d4-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="c03d4-103">Volá se službami CLR (Common Language Runtime) k načtení metadat obrázku.</span><span class="sxs-lookup"><span data-stu-id="c03d4-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c03d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c03d4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c03d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c03d4-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="c03d4-106">pro Řetězec, který určuje cestu k souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="c03d4-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="c03d4-107">pro Časové razítko souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="c03d4-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="c03d4-108">pro Velikost souboru obrázku</span><span class="sxs-lookup"><span data-stu-id="c03d4-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="c03d4-109">pro Globálně jedinečný identifikátor obrázku.</span><span class="sxs-lookup"><span data-stu-id="c03d4-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="c03d4-110">pro Relativní virtuální adresa (RVA) metadat.</span><span class="sxs-lookup"><span data-stu-id="c03d4-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="c03d4-111">Adresa je relativní vzhledem k základní adrese obrázku.</span><span class="sxs-lookup"><span data-stu-id="c03d4-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="c03d4-112">pro Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="c03d4-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="c03d4-113">pro Velikost vyrovnávací paměti, do které se mají umístit metadata</span><span class="sxs-lookup"><span data-stu-id="c03d4-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c03d4-114">mimo Vyrovnávací paměť, do které se mají umístit metadata</span><span class="sxs-lookup"><span data-stu-id="c03d4-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="c03d4-115">mimo Velikost vrácených metadat.</span><span class="sxs-lookup"><span data-stu-id="c03d4-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c03d4-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c03d4-116">Remarks</span></span>  
 <span data-ttu-id="c03d4-117">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c03d4-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c03d4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c03d4-118">Requirements</span></span>  
 <span data-ttu-id="c03d4-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c03d4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c03d4-120">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="c03d4-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c03d4-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c03d4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c03d4-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c03d4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c03d4-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c03d4-123">See also</span></span>

- [<span data-ttu-id="c03d4-124">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c03d4-124">ICLRMetadataLocator Interface</span></span>](iclrmetadatalocator-interface.md)
