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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 193abe173b259ff2679642e229fce96151e37872
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179674"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="f196f-102">IMetaDataImport::EnumSignatures – metoda</span><span class="sxs-lookup"><span data-stu-id="f196f-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="f196f-103">Vytvoří výčet tokenů podpisu představující samostatné podpisy v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="f196f-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f196f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f196f-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f196f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f196f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f196f-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="f196f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f196f-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="f196f-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="f196f-108">[out] Pole pro ukládání tokenů podpisu.</span><span class="sxs-lookup"><span data-stu-id="f196f-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f196f-109">[in] Maximální velikost `rSignatures` pole.</span><span class="sxs-lookup"><span data-stu-id="f196f-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="f196f-110">[out] Počet tokenů podpisu pro vrácené v `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="f196f-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f196f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f196f-111">Return Value</span></span>  
  
|<span data-ttu-id="f196f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f196f-112">HRESULT</span></span>|<span data-ttu-id="f196f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f196f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f196f-114">`EnumSignatures` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f196f-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f196f-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="f196f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f196f-116">V takovém případě `pcSignatures` je nula.</span><span class="sxs-lookup"><span data-stu-id="f196f-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f196f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f196f-117">Remarks</span></span>  
 <span data-ttu-id="f196f-118">Podpis tokeny jsou vytvářeny [imetadataemit::gettokenfromsig –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f196f-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f196f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f196f-119">Requirements</span></span>  
 <span data-ttu-id="f196f-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f196f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f196f-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f196f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f196f-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f196f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f196f-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f196f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f196f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f196f-124">See also</span></span>

- [<span data-ttu-id="f196f-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f196f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f196f-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f196f-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
