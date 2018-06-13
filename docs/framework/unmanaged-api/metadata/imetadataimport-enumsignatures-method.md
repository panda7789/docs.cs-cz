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
ms.openlocfilehash: d36270047c8af0580a1cc3b44aa303e5907f33fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448117"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="c9ed5-102">IMetaDataImport::EnumSignatures – metoda</span><span class="sxs-lookup"><span data-stu-id="c9ed5-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="c9ed5-103">Vytvoří výčet podpis tokeny představující samostatné podpisy v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ed5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9ed5-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9ed5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9ed5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c9ed5-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c9ed5-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="c9ed5-108">[out] Pole používá k ukládání tokeny podpis.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c9ed5-109">[v] Maximální velikost `rSignatures` pole.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="c9ed5-110">[out] Počet podpis tokeny, vrátí se v `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9ed5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c9ed5-111">Return Value</span></span>  
  
|<span data-ttu-id="c9ed5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9ed5-112">HRESULT</span></span>|<span data-ttu-id="c9ed5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c9ed5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c9ed5-114">`EnumSignatures` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c9ed5-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c9ed5-116">V takovém případě `pcSignatures` je nulová.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9ed5-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9ed5-117">Remarks</span></span>  
 <span data-ttu-id="c9ed5-118">Podpis tokeny jsou vytvořené pomocí [imetadataemit::gettokenfromsig –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="c9ed5-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9ed5-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9ed5-119">Requirements</span></span>  
 <span data-ttu-id="c9ed5-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9ed5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9ed5-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9ed5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9ed5-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9ed5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9ed5-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9ed5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ed5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9ed5-124">See Also</span></span>  
 [<span data-ttu-id="c9ed5-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9ed5-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c9ed5-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9ed5-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
