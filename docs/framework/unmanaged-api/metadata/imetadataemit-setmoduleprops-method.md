---
title: IMetaDataEmit::SetModuleProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: aee258c49e6726ebef990257456fd273b01b9ef0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007842"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="6e55a-102">IMetaDataEmit::SetModuleProps – metoda</span><span class="sxs-lookup"><span data-stu-id="6e55a-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="6e55a-103">Aktualizuje odkazy na modul definovaný předchozím voláním [IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="6e55a-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e55a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e55a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e55a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e55a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="6e55a-106">pro Název modulu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6e55a-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="6e55a-107">Toto je pouze název souboru, nikoli název úplné cesty.</span><span class="sxs-lookup"><span data-stu-id="6e55a-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e55a-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e55a-108">Requirements</span></span>  
 <span data-ttu-id="6e55a-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e55a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e55a-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6e55a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e55a-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="6e55a-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e55a-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e55a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e55a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e55a-113">See also</span></span>

- [<span data-ttu-id="6e55a-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e55a-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6e55a-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e55a-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
