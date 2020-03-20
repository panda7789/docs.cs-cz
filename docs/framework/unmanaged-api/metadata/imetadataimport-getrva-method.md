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
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177216"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="a63fb-102">IMetaDataImport::GetRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="a63fb-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="a63fb-103">Získá relativní virtuální adresu (RVA) a příznaky implementace metody nebo pole reprezentované zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="a63fb-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a63fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a63fb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a63fb-106">[v] A MethodDef nebo FieldDef token metadat, který představuje objekt kódu vrátit RVA pro.</span><span class="sxs-lookup"><span data-stu-id="a63fb-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="a63fb-107">Pokud je token FieldDef, pole musí být globální proměnná.</span><span class="sxs-lookup"><span data-stu-id="a63fb-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="a63fb-108">[out] Ukazatel na relativní virtuální adresu objektu kódu reprezentovaného tokenem.</span><span class="sxs-lookup"><span data-stu-id="a63fb-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="a63fb-109">[out] Ukazatel na příznaky implementace pro metodu.</span><span class="sxs-lookup"><span data-stu-id="a63fb-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="a63fb-110">Tato hodnota je bitová maska z [cormethodimpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="a63fb-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="a63fb-111">Hodnota je `pdwImplFlags` platná pouze `tk` v případě, že je token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="a63fb-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a63fb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a63fb-112">Requirements</span></span>  
 <span data-ttu-id="a63fb-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a63fb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a63fb-114">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="a63fb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a63fb-115">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a63fb-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a63fb-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a63fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63fb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a63fb-117">See also</span></span>

- [<span data-ttu-id="a63fb-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a63fb-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a63fb-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a63fb-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
