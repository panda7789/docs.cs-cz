---
title: IMetaDataTables::GetUserStringHeapSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 1aea017f17e29544e9288e1f57e6f84f9a2f6dae
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501102"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="f953f-102">IMetaDataTables::GetUserStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="f953f-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="f953f-103">Získá velikost haldy řetězců uživatele v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f953f-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f953f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f953f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f953f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f953f-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="f953f-106">mimo Ukazatel na velikost haldy řetězců uživatele v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f953f-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f953f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f953f-107">Requirements</span></span>  
 <span data-ttu-id="f953f-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f953f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f953f-109">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f953f-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f953f-110">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f953f-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f953f-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f953f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f953f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f953f-112">See also</span></span>

- [<span data-ttu-id="f953f-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f953f-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="f953f-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f953f-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
