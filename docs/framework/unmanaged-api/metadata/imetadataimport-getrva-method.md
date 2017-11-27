---
title: "IMetaDataImport::GetRVA – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetRVA
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f64cc5b0aa6043c5408868a5a6bf23e24278ea26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="1ee83-102">IMetaDataImport::GetRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="1ee83-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="1ee83-103">Získá relativní virtuální adresy (RVA) a příznaky implementace metody nebo pole reprezentována zadaný token.</span><span class="sxs-lookup"><span data-stu-id="1ee83-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ee83-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ee83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ee83-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1ee83-106">[v] MethodDef nebo FieldDef metadata token, který představuje objekt kód, který chcete vrátit RVA pro.</span><span class="sxs-lookup"><span data-stu-id="1ee83-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="1ee83-107">Pokud je token FieldDef, v poli musí být globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="1ee83-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="1ee83-108">[out] Ukazatel na relativní virtuální adresu kód objekt reprezentovaný rozhraním token.</span><span class="sxs-lookup"><span data-stu-id="1ee83-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="1ee83-109">[out] Ukazatel na implementaci příznaky pro metodu.</span><span class="sxs-lookup"><span data-stu-id="1ee83-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="1ee83-110">Tato hodnota je bitová maska z [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="1ee83-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="1ee83-111">Hodnota `pdwImplFlags` je platná pouze v případě `tk` je MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="1ee83-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee83-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ee83-112">Requirements</span></span>  
 <span data-ttu-id="1ee83-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ee83-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee83-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ee83-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ee83-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ee83-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ee83-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee83-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee83-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ee83-117">See Also</span></span>  
 [<span data-ttu-id="1ee83-118">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ee83-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1ee83-119">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ee83-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
