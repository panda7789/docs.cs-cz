---
title: IMetaDataImport::GetRVA – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d305aa59c1b9e9e1225b30f12e36fc689d584db1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778882"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="816ed-102">IMetaDataImport::GetRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="816ed-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="816ed-103">Získá relativní virtuální adresu (RVA) a příznaky implementace metody nebo pole reprezentována zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="816ed-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="816ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="816ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="816ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="816ed-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="816ed-106">[in] MethodDef či FieldDef token metadat, který představuje objekt kódu se vraťte adresu RVA pro.</span><span class="sxs-lookup"><span data-stu-id="816ed-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="816ed-107">Pokud je token FieldDef, pole musí být globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="816ed-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="816ed-108">[out] Ukazatel na relativní virtuální adresu kód objektu reprezentovaného parametrem tokenu.</span><span class="sxs-lookup"><span data-stu-id="816ed-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="816ed-109">[out] Ukazatel na implementaci příznaky pro metodu.</span><span class="sxs-lookup"><span data-stu-id="816ed-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="816ed-110">Tato hodnota je bitová maska z [cormethodimpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="816ed-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="816ed-111">Hodnota `pdwImplFlags` je platný pouze tehdy, pokud `tk` je MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="816ed-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="816ed-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="816ed-112">Requirements</span></span>  
 <span data-ttu-id="816ed-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="816ed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="816ed-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="816ed-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="816ed-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="816ed-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="816ed-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="816ed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816ed-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="816ed-117">See also</span></span>

- [<span data-ttu-id="816ed-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="816ed-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="816ed-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="816ed-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
