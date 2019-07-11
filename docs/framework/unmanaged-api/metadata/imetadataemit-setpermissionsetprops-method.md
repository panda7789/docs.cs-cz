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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f77e6e9711f05262e494f2814750af8ef7cd9f64
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750900"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="8dcee-102">IMetaDataEmit::SetPermissionSetProps – metoda</span><span class="sxs-lookup"><span data-stu-id="8dcee-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="8dcee-103">Nastaví nebo aktualizuje podpis metadat sady oprávnění určené předchozím volání funkce [imetadataemit::definepermissionset –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="8dcee-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dcee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dcee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dcee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dcee-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="8dcee-106">[in] Token metadat, který představuje objekt, který má být upravena.</span><span class="sxs-lookup"><span data-stu-id="8dcee-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="8dcee-107">[in] A [cordeclsecurity –](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) hodnotu, která určuje typ deklarativní zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="8dcee-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="8dcee-108">[in] Zabezpečovací BLOB.</span><span class="sxs-lookup"><span data-stu-id="8dcee-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="8dcee-109">[in] Velikost v bajtech, z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="8dcee-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="8dcee-110">[out] `mdPermission` Token metadat, který představuje aktualizovanými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="8dcee-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dcee-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8dcee-111">Requirements</span></span>  
 <span data-ttu-id="8dcee-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dcee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dcee-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8dcee-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8dcee-114">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8dcee-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8dcee-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dcee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dcee-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8dcee-116">See also</span></span>

- [<span data-ttu-id="8dcee-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8dcee-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8dcee-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8dcee-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
