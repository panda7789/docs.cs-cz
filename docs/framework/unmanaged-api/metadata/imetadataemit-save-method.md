---
title: IMetaDataEmit::Save – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: 23f6a301c4c11be92e05dbac0d4f69817d857a28
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003939"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="e639e-102">IMetaDataEmit::Save – metoda</span><span class="sxs-lookup"><span data-stu-id="e639e-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="e639e-103">Uloží všechna metadata v aktuálním oboru do souboru na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="e639e-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e639e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e639e-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e639e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e639e-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="e639e-106">pro Název souboru, do kterého se má uložit.</span><span class="sxs-lookup"><span data-stu-id="e639e-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="e639e-107">Pokud je tato hodnota null, kopie v paměti bude uložena do posledního používaného umístění.</span><span class="sxs-lookup"><span data-stu-id="e639e-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="e639e-108">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="e639e-108">[in] Reserved.</span></span> <span data-ttu-id="e639e-109">Musí mít hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="e639e-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e639e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e639e-110">Requirements</span></span>  
 <span data-ttu-id="e639e-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e639e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e639e-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e639e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e639e-113">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e639e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e639e-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e639e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e639e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e639e-115">See also</span></span>

- [<span data-ttu-id="e639e-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e639e-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e639e-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e639e-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
