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
ms.openlocfilehash: d3e25f271fc434785e25e7b226ad98f86b5f8dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492782"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="15429-102">IMetaDataEmit2::SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="15429-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="15429-103">Uloží změny z aktuální relace úprav a pokračování do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="15429-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15429-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15429-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15429-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15429-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="15429-106">pro Název souboru, pod kterým chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="15429-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="15429-107">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="15429-107">[in] Reserved.</span></span> <span data-ttu-id="15429-108">Musí mít hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="15429-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15429-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15429-109">Requirements</span></span>  
 <span data-ttu-id="15429-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15429-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15429-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="15429-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15429-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="15429-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15429-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15429-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15429-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15429-114">See also</span></span>

- [<span data-ttu-id="15429-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15429-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="15429-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15429-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
