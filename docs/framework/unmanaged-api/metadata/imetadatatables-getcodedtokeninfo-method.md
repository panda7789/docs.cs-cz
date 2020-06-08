---
title: IMetaDataTables::GetCodedTokenInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
ms.openlocfilehash: 8ab16ad5b2b2838125e07511ef47be737f40671c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501206"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="f4704-102">IMetaDataTables::GetCodedTokenInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="f4704-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="f4704-103">Získá ukazatel na pole tokenů přidružené k zadanému indexu řádků.</span><span class="sxs-lookup"><span data-stu-id="f4704-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4704-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4704-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4704-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4704-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="f4704-106">pro Druh kódovaného tokenu, který se má vrátit</span><span class="sxs-lookup"><span data-stu-id="f4704-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f4704-107">mimo Ukazatel na délku `ppTokens` .</span><span class="sxs-lookup"><span data-stu-id="f4704-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="f4704-108">mimo Ukazatel na ukazatel na pole, které obsahuje seznam vrácených tokenů.</span><span class="sxs-lookup"><span data-stu-id="f4704-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="f4704-109">mimo Ukazatel na ukazatel na název tokenu na adrese `ixCdTkn` .</span><span class="sxs-lookup"><span data-stu-id="f4704-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4704-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4704-110">Requirements</span></span>  
 <span data-ttu-id="f4704-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4704-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4704-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f4704-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4704-113">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f4704-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4704-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4704-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4704-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4704-115">See also</span></span>

- [<span data-ttu-id="f4704-116">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4704-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="f4704-117">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4704-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
