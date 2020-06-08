---
title: IMetaDataTables::GetStringHeapSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
ms.openlocfilehash: 1aa7853602c1aaf484ef89d9c4fb06464e135f80
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501158"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="caa71-102">IMetaDataTables::GetStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="caa71-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="caa71-103">Získá velikost haldy řetězce v bajtech.</span><span class="sxs-lookup"><span data-stu-id="caa71-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caa71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caa71-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="caa71-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="caa71-106">mimo Ukazatel na velikost haldy řetězce v bajtech.</span><span class="sxs-lookup"><span data-stu-id="caa71-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caa71-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="caa71-107">Requirements</span></span>  
 <span data-ttu-id="caa71-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caa71-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa71-109">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="caa71-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="caa71-110">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="caa71-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="caa71-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa71-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa71-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caa71-112">See also</span></span>

- [<span data-ttu-id="caa71-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caa71-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="caa71-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caa71-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
