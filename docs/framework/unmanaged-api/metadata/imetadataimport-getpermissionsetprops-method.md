---
title: IMetaDataImport::GetPermissionSetProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 806f1ebcacb9e7ad27b7370f9976b3341bf64f8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466931"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="f952f-102">IMetaDataImport::GetPermissionSetProps – metoda</span><span class="sxs-lookup"><span data-stu-id="f952f-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="f952f-103">Získá metadata přidružená k <xref:System.Security.PermissionSet?displayProperty=nameWithType> reprezentována zadaný token oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f952f-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f952f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f952f-104">Syntax</span></span>  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f952f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f952f-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="f952f-106">[in] Token metadat oprávnění, který představuje sadu k získání vlastností metadat pro oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f952f-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="f952f-107">[out] Ukazatel na sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f952f-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="f952f-108">[out] Ukazatel na podpis binárního metadata sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f952f-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="f952f-109">[out] Velikost v bajtech `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="f952f-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f952f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f952f-110">Requirements</span></span>  
 <span data-ttu-id="f952f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f952f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f952f-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f952f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f952f-113">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f952f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f952f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f952f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f952f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f952f-115">See also</span></span>
- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="f952f-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f952f-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f952f-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f952f-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
