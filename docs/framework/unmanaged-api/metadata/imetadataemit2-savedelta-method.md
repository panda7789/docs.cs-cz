---
title: IMetaDataEmit2::SaveDelta – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: 0ebcab7a759b64bfbb254df1c1aa339cde77d054
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175561"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="1b31a-102">IMetaDataEmit2::SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="1b31a-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="1b31a-103">Uloží změny z aktuální relace úprav a pokračování do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="1b31a-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b31a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b31a-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b31a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b31a-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="1b31a-106">[v] Název souboru, pod kterým chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="1b31a-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="1b31a-107">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="1b31a-107">[in] Reserved.</span></span> <span data-ttu-id="1b31a-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="1b31a-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b31a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b31a-109">Requirements</span></span>  
 <span data-ttu-id="1b31a-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b31a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b31a-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="1b31a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b31a-112">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b31a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b31a-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b31a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b31a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b31a-114">See also</span></span>

- [<span data-ttu-id="1b31a-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b31a-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="1b31a-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b31a-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
