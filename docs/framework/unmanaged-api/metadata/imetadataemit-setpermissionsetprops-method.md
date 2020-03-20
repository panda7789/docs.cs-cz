---
title: IMetaDataEmit::SetPermissionSetProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: de4cfdf2a9353eebdebaf4df9e481d06d776ff04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177491"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="744cd-102">IMetaDataEmit::SetPermissionSetProps – metoda</span><span class="sxs-lookup"><span data-stu-id="744cd-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="744cd-103">Nastaví nebo aktualizuje funkce podpisu metadat sady oprávnění definované předchozím voláním [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="744cd-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="744cd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="744cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="744cd-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="744cd-106">[v] Token metadat, který představuje objekt, který má být dekorován.</span><span class="sxs-lookup"><span data-stu-id="744cd-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="744cd-107">[v] Hodnota [CorDeclSecurity,](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) která určuje typ deklarativního zabezpečení, které má být použito.</span><span class="sxs-lookup"><span data-stu-id="744cd-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="744cd-108">[v] Oprávnění BLOB.</span><span class="sxs-lookup"><span data-stu-id="744cd-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="744cd-109">[v] Velikost v bajtů `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="744cd-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="744cd-110">[out] Token `mdPermission` metadat, který představuje aktualizovaná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="744cd-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="744cd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="744cd-111">Requirements</span></span>  
 <span data-ttu-id="744cd-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="744cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="744cd-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="744cd-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="744cd-114">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="744cd-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="744cd-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="744cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744cd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="744cd-116">See also</span></span>

- [<span data-ttu-id="744cd-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="744cd-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="744cd-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="744cd-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
