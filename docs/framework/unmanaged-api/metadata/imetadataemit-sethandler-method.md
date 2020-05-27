---
title: IMetaDataEmit::SetHandler – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 4fa227d18b8cb10936d93fda9bcaf413ce63ca3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003932"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="da58a-102">IMetaDataEmit::SetHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="da58a-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="da58a-103">Nastaví metodu, na kterou odkazuje zadaný `IUnknown` ukazatel jako zpětné volání oznámení pro přemapování tokenů.</span><span class="sxs-lookup"><span data-stu-id="da58a-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da58a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da58a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da58a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da58a-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="da58a-106">pro Obslužná rutina, která se má zaregistrovat</span><span class="sxs-lookup"><span data-stu-id="da58a-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da58a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da58a-107">Remarks</span></span>  
 <span data-ttu-id="da58a-108">Modul metadat odesílá oznámení pomocí metody, která je poskytována `SetHandler` , na kompilátory, které negenerují záznamy optimalizovaným způsobem a které by chtěli optimalizovat uložené záznamy.</span><span class="sxs-lookup"><span data-stu-id="da58a-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="da58a-109">Pokud není metoda zpětného volání poskytována prostřednictvím `SetHandler` , nebude provedena žádná optimalizace při uložení, s výjimkou případů, kdy byl pro každý obor sloučeno několik importovaných oborů pomocí `IMapToken` sloučení.</span><span class="sxs-lookup"><span data-stu-id="da58a-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da58a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da58a-110">Requirements</span></span>  
 <span data-ttu-id="da58a-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da58a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da58a-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="da58a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da58a-113">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="da58a-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da58a-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da58a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da58a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="da58a-115">See also</span></span>

- [<span data-ttu-id="da58a-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da58a-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="da58a-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da58a-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
