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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 212625fd460e88201dd4799754297861826d3aa7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777143"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="4e203-102">IMetaDataEmit2::SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="4e203-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="4e203-103">Uloží změny z aktuální relace edit-and-continue do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="4e203-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e203-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e203-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e203-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e203-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="4e203-106">[in] Název souboru v rámci kterého chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="4e203-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="4e203-107">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="4e203-107">[in] Reserved.</span></span> <span data-ttu-id="4e203-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="4e203-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e203-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e203-109">Requirements</span></span>  
 <span data-ttu-id="4e203-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e203-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e203-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4e203-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e203-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e203-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e203-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e203-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e203-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e203-114">See also</span></span>

- [<span data-ttu-id="4e203-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e203-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="4e203-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e203-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
