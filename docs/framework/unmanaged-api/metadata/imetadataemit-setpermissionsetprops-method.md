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
ms.openlocfilehash: 510c33b8e0e26bead00dcb85a6ceba102a5f267d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163771"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="c3e1f-102">IMetaDataEmit::SetPermissionSetProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c3e1f-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="c3e1f-103">Nastaví nebo aktualizuje podpis metadat sady oprávnění určené předchozím volání funkce [imetadataemit::definepermissionset –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3e1f-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3e1f-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3e1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3e1f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c3e1f-106">[in] Token metadat, který představuje objekt, který má být upravena.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="c3e1f-107">[in] A [cordeclsecurity –](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) hodnotu, která určuje typ deklarativní zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="c3e1f-108">[in] Zabezpečovací BLOB.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="c3e1f-109">[in] Velikost v bajtech, z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="c3e1f-110">[out] `mdPermission` Token metadat, který představuje aktualizovanými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e1f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3e1f-111">Requirements</span></span>  
 <span data-ttu-id="c3e1f-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3e1f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3e1f-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3e1f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3e1f-114">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3e1f-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c3e1f-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c3e1f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3e1f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3e1f-116">See also</span></span>

- [<span data-ttu-id="c3e1f-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3e1f-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c3e1f-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3e1f-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
