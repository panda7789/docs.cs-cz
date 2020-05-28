---
title: IMetaDataEmit::SaveToStream – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 87e00a69643b6bc403188fb0fdb6f9e3f3d82115
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003871"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="e4b80-102">IMetaDataEmit::SaveToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="e4b80-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="e4b80-103">Uloží všechna metadata v aktuálním oboru do určeného `IStream` .</span><span class="sxs-lookup"><span data-stu-id="e4b80-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4b80-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4b80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4b80-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="e4b80-106">pro Zapisovatelný datový proud, do kterého se mají ukládat.</span><span class="sxs-lookup"><span data-stu-id="e4b80-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="e4b80-107">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="e4b80-107">[in] Reserved.</span></span> <span data-ttu-id="e4b80-108">Musí mít hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="e4b80-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4b80-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4b80-109">Requirements</span></span>  
 <span data-ttu-id="e4b80-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4b80-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4b80-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e4b80-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4b80-112">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e4b80-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4b80-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4b80-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b80-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4b80-114">See also</span></span>

- [<span data-ttu-id="e4b80-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4b80-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e4b80-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4b80-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
