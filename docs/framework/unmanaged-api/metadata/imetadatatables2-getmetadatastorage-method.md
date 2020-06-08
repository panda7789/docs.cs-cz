---
title: IMetaDataTables2::GetMetaDataStorage – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: 55fcde6c47705e515eb2d20f25ac870e257b92c0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501128"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="14119-102">IMetaDataTables2::GetMetaDataStorage – metoda</span><span class="sxs-lookup"><span data-stu-id="14119-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="14119-103">Získá velikost a obsah metadat uložených v zadaném oddílu.</span><span class="sxs-lookup"><span data-stu-id="14119-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14119-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14119-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14119-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14119-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="14119-106">[in, out] Ukazatel na oddíl metadat.</span><span class="sxs-lookup"><span data-stu-id="14119-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="14119-107">mimo Velikost datového proudu metadat.</span><span class="sxs-lookup"><span data-stu-id="14119-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14119-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14119-108">Requirements</span></span>  
 <span data-ttu-id="14119-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14119-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14119-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="14119-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14119-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="14119-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14119-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14119-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14119-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14119-113">See also</span></span>

- [<span data-ttu-id="14119-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14119-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="14119-115">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14119-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
