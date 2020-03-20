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
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177546"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="17de9-102">IMetaDataEmit::SetHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="17de9-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="17de9-103">Nastaví metodu, na `IUnknown` kterou zadaný ukazatel odkazuje jako zpětné volání oznámení pro přemapování tokenů.</span><span class="sxs-lookup"><span data-stu-id="17de9-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17de9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17de9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17de9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17de9-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="17de9-106">[v] Obslužná rutina k registraci.</span><span class="sxs-lookup"><span data-stu-id="17de9-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17de9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17de9-107">Remarks</span></span>  
 <span data-ttu-id="17de9-108">Modul metadat odešle oznámení pomocí metody, která `SetHandler`je poskytována aplikace , kompilátorům, které negenerují záznamy optimalizovaným způsobem a které by chtěly optimalizovat uložené záznamy.</span><span class="sxs-lookup"><span data-stu-id="17de9-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="17de9-109">Pokud metoda zpětného volání není `SetHandler`k dispozici prostřednictvím , žádná optimalizace bude provedena `IMapToken` na uložit s výjimkou případů, kdy několik oborů importu byly sloučeny pomocí sloučení pro každý obor.</span><span class="sxs-lookup"><span data-stu-id="17de9-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17de9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17de9-110">Requirements</span></span>  
 <span data-ttu-id="17de9-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17de9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17de9-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="17de9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17de9-113">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17de9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17de9-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17de9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17de9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="17de9-115">See also</span></span>

- [<span data-ttu-id="17de9-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17de9-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="17de9-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17de9-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
