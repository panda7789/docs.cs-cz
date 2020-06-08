---
title: IMetaDataImport::EnumUserStrings – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: cd164008098c053e7d6506a6eef7d3bc8e4274b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503694"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="ea366-102">IMetaDataImport::EnumUserStrings – metoda</span><span class="sxs-lookup"><span data-stu-id="ea366-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="ea366-103">Vytvoří výčet řetězcových tokenů představujících pevně zakódované řetězce v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="ea366-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea366-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea366-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea366-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea366-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ea366-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="ea366-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ea366-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="ea366-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="ea366-108">mimo Pole použité pro uložení řetězcových tokenů.</span><span class="sxs-lookup"><span data-stu-id="ea366-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ea366-109">pro Maximální velikost `rStrings` pole.</span><span class="sxs-lookup"><span data-stu-id="ea366-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="ea366-110">mimo Počet řetězcových tokenů vrácených v `rStrings` .</span><span class="sxs-lookup"><span data-stu-id="ea366-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea366-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ea366-111">Return Value</span></span>  
  
|<span data-ttu-id="ea366-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea366-112">HRESULT</span></span>|<span data-ttu-id="ea366-113">Description</span><span class="sxs-lookup"><span data-stu-id="ea366-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ea366-114">`EnumUserStrings`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ea366-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ea366-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="ea366-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="ea366-116">V takovém případě `pcStrings` je nula.</span><span class="sxs-lookup"><span data-stu-id="ea366-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea366-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea366-117">Remarks</span></span>  
 <span data-ttu-id="ea366-118">Řetězcové tokeny jsou vytvořeny metodou [IMetaDataEmit::D efineuserstring](imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ea366-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="ea366-119">Tato metoda je navržena tak, aby byla používána prohlížečem metadat, nikoli kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="ea366-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea366-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea366-120">Requirements</span></span>  
 <span data-ttu-id="ea366-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea366-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea366-122">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ea366-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea366-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea366-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea366-124">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea366-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea366-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea366-125">See also</span></span>

- [<span data-ttu-id="ea366-126">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea366-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ea366-127">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea366-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
