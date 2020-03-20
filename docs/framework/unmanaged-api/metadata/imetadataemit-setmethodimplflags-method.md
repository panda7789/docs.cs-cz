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
ms.openlocfilehash: 7ed7770f26ea4620d79f3be3f67e72f73c75057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175626"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="fdbed-102">IMetaDataEmit::SetMethodImplFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="fdbed-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="fdbed-103">Nastaví nebo aktualizuje podpis metadat implementace zděděné metody, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="fdbed-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdbed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdbed-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdbed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdbed-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="fdbed-106">[v] Token pro metodu, která má být změněna.</span><span class="sxs-lookup"><span data-stu-id="fdbed-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="fdbed-107">[v] Kombinace hodnot [cormethodimpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčtu, který určuje funkce implementace metody.</span><span class="sxs-lookup"><span data-stu-id="fdbed-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdbed-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdbed-108">Requirements</span></span>  
 <span data-ttu-id="fdbed-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdbed-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdbed-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="fdbed-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fdbed-111">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fdbed-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdbed-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdbed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdbed-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdbed-113">See also</span></span>

- [<span data-ttu-id="fdbed-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdbed-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fdbed-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdbed-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
