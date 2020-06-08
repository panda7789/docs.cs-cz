---
title: IMetaDataEmit2::GetDeltaSaveSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 24fe8fd65b36e133b767cd07c8602aa1ea7b9dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493094"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="e1d0b-102">IMetaDataEmit2::GetDeltaSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e1d0b-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="e1d0b-103">Získá hodnotu označující změnu velikosti metadat, která je výsledkem aktuální relace Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="e1d0b-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1d0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1d0b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1d0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1d0b-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="e1d0b-106">pro Jedna z hodnot [CorSaveSize –](corsavesize-enumeration.md) , která určuje požadovanou úroveň přesnosti.</span><span class="sxs-lookup"><span data-stu-id="e1d0b-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="e1d0b-107">Pro .NET Framework verze 2,0 se tento parametr ignoruje.</span><span class="sxs-lookup"><span data-stu-id="e1d0b-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="e1d0b-108">mimo Změna velikosti metadat.</span><span class="sxs-lookup"><span data-stu-id="e1d0b-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1d0b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1d0b-109">Requirements</span></span>  
 <span data-ttu-id="e1d0b-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1d0b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1d0b-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e1d0b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1d0b-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e1d0b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1d0b-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1d0b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d0b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1d0b-114">See also</span></span>

- [<span data-ttu-id="e1d0b-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1d0b-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="e1d0b-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1d0b-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
