---
title: IMetaDataEmit::SetMethodImplFlags – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: a02456393680169ce33369ee5914f6c5216081c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009215"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="f9c93-102">IMetaDataEmit::SetMethodImplFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="f9c93-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="f9c93-103">Nastaví nebo aktualizuje podpis metadat zděděné implementace metody, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="f9c93-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c93-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9c93-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9c93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9c93-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f9c93-106">pro Token pro metodu, která má být změněna.</span><span class="sxs-lookup"><span data-stu-id="f9c93-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="f9c93-107">pro Kombinace hodnot výčtu [CorMethodImpl –](cormethodimpl-enumeration.md) , která určuje funkce implementace metody.</span><span class="sxs-lookup"><span data-stu-id="f9c93-107">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c93-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9c93-108">Requirements</span></span>  
 <span data-ttu-id="f9c93-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9c93-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9c93-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f9c93-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9c93-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f9c93-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9c93-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9c93-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c93-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9c93-113">See also</span></span>

- [<span data-ttu-id="f9c93-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9c93-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f9c93-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9c93-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
