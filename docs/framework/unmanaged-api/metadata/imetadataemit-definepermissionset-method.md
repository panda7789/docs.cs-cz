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
ms.openlocfilehash: a0fd3fdb6dde9fd6b88ea6c64ed907c8a3e9e46d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175795"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="bddbd-102">IMetaDataEmit::DefinePermissionSet – metoda</span><span class="sxs-lookup"><span data-stu-id="bddbd-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="bddbd-103">Vytvoří definici sady oprávnění se zadaným podpisem metadat a získá token k této definici sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="bddbd-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bddbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bddbd-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bddbd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bddbd-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bddbd-106">[v] Objekt, který má být dekorován.</span><span class="sxs-lookup"><span data-stu-id="bddbd-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="bddbd-107">[v] Hodnota [CorDeclSecurity,](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) která určuje typ deklarativního zabezpečení, které má být použito.</span><span class="sxs-lookup"><span data-stu-id="bddbd-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="bddbd-108">[v] Oprávnění BLOB.</span><span class="sxs-lookup"><span data-stu-id="bddbd-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="bddbd-109">[v] Velikost v bajtů `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="bddbd-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="bddbd-110">[out] Vrácený token oprávnění.</span><span class="sxs-lookup"><span data-stu-id="bddbd-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bddbd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bddbd-111">Requirements</span></span>  
 <span data-ttu-id="bddbd-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bddbd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bddbd-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="bddbd-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bddbd-114">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bddbd-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bddbd-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bddbd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bddbd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bddbd-116">See also</span></span>

- [<span data-ttu-id="bddbd-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bddbd-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bddbd-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bddbd-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
