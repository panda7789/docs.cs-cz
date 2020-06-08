---
title: IMetaDataImport::EnumSignatures – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 652ebf1be6a58e08da27aaed5b2e84a8f2aee98a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503767"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="b8ab8-102">IMetaDataImport::EnumSignatures – metoda</span><span class="sxs-lookup"><span data-stu-id="b8ab8-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="b8ab8-103">Vytvoří výčet tokenů podpisu představujících samostatné podpisy v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="b8ab8-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8ab8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8ab8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8ab8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8ab8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b8ab8-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b8ab8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b8ab8-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="b8ab8-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="b8ab8-108">mimo Pole, které se používá k uložení tokenů podpisu.</span><span class="sxs-lookup"><span data-stu-id="b8ab8-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b8ab8-109">pro Maximální velikost `rSignatures` pole.</span><span class="sxs-lookup"><span data-stu-id="b8ab8-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="b8ab8-110">mimo Počet tokenů podpisu vrácených v `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="b8ab8-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8ab8-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8ab8-111">Return Value</span></span>  
  
|<span data-ttu-id="b8ab8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8ab8-112">HRESULT</span></span>|<span data-ttu-id="b8ab8-113">Description</span><span class="sxs-lookup"><span data-stu-id="b8ab8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b8ab8-114">`EnumSignatures`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b8ab8-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b8ab8-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="b8ab8-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b8ab8-116">V takovém případě `pcSignatures` je nula.</span><span class="sxs-lookup"><span data-stu-id="b8ab8-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8ab8-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8ab8-117">Remarks</span></span>  
 <span data-ttu-id="b8ab8-118">Tokeny podpisu jsou vytvořeny metodou [IMetaDataEmit:: GetTokenFromSig –](imetadataemit-gettokenfromsig-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b8ab8-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8ab8-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8ab8-119">Requirements</span></span>  
 <span data-ttu-id="b8ab8-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8ab8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8ab8-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b8ab8-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8ab8-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b8ab8-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8ab8-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8ab8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ab8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8ab8-124">See also</span></span>

- [<span data-ttu-id="b8ab8-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8ab8-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b8ab8-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8ab8-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
