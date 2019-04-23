---
title: IMetaDataEmit::DefinePermissionSet – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33eadccf691b14289a46ff460f3cef8ae636b129
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074843"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="205c6-102">IMetaDataEmit::DefinePermissionSet – metoda</span><span class="sxs-lookup"><span data-stu-id="205c6-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="205c6-103">Vytvoří definici sada oprávnění s podpisem Zadaná metadata a získá token pro tuto definici sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="205c6-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="205c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="205c6-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="205c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="205c6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="205c6-106">[in] Objekt, který chcete být upravena.</span><span class="sxs-lookup"><span data-stu-id="205c6-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="205c6-107">[in] A [cordeclsecurity –](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) hodnotu, která určuje typ deklarativní zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="205c6-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="205c6-108">[in] Zabezpečovací BLOB.</span><span class="sxs-lookup"><span data-stu-id="205c6-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="205c6-109">[in] Velikost v bajtech, z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="205c6-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="205c6-110">[out] Token vrácený oprávnění.</span><span class="sxs-lookup"><span data-stu-id="205c6-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="205c6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="205c6-111">Requirements</span></span>  
 <span data-ttu-id="205c6-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="205c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="205c6-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="205c6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="205c6-114">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="205c6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="205c6-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="205c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205c6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="205c6-116">See also</span></span>

- [<span data-ttu-id="205c6-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="205c6-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="205c6-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="205c6-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
