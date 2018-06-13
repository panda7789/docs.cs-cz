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
ms.openlocfilehash: 8d80e3206f74c3c50c8436563b0e39d1229a963b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446366"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="d18e2-102">IMetaDataEmit::SetPermissionSetProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d18e2-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="d18e2-103">Nastaví nebo aktualizuje funkce metadata podpis sadu oprávnění definovanou před voláním [imetadataemit::definepermissionset –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="d18e2-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d18e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d18e2-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d18e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d18e2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d18e2-106">[v] Metadata token, který představuje objekt, který má být doplněný o atribut.</span><span class="sxs-lookup"><span data-stu-id="d18e2-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="d18e2-107">[v] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) hodnotu, která určuje typ deklarativní zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="d18e2-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="d18e2-108">[v] Oprávnění objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="d18e2-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="d18e2-109">[v] Velikost v bajtech z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="d18e2-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="d18e2-110">[out] `mdPermission` Metadata token, který představuje aktualizované oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d18e2-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d18e2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d18e2-111">Requirements</span></span>  
 <span data-ttu-id="d18e2-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d18e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d18e2-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d18e2-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d18e2-114">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d18e2-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d18e2-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d18e2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18e2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d18e2-116">See Also</span></span>  
 [<span data-ttu-id="d18e2-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d18e2-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d18e2-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d18e2-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
