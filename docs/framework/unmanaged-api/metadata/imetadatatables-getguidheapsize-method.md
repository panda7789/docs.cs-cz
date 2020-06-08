---
title: IMetaDataTables::GetGuidHeapSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
ms.openlocfilehash: 71a75defa72e4fe3594b4d0ceff45273b3a35395
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490351"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="93d14-102">IMetaDataTables::GetGuidHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="93d14-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="93d14-103">Získá velikost haldy GUID (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="93d14-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93d14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93d14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93d14-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="93d14-106">mimo Ukazatel na velikost haldy GUID v bajtech.</span><span class="sxs-lookup"><span data-stu-id="93d14-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93d14-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93d14-107">Requirements</span></span>  
 <span data-ttu-id="93d14-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93d14-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93d14-109">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="93d14-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93d14-110">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="93d14-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="93d14-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d14-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d14-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93d14-112">See also</span></span>

- [<span data-ttu-id="93d14-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93d14-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="93d14-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93d14-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
