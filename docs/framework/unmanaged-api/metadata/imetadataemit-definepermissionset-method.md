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
ms.openlocfilehash: 05339787b112ad029cb9870e8c6ffca37e55e631
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445186"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="90c19-102">IMetaDataEmit::DefinePermissionSet – metoda</span><span class="sxs-lookup"><span data-stu-id="90c19-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="90c19-103">Vytvoří definici oprávnění nastavit podpisem Zadaná metadata a získá token pro tuto definici sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="90c19-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90c19-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90c19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90c19-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="90c19-106">[v] Objekt, který má být doplněný o atribut.</span><span class="sxs-lookup"><span data-stu-id="90c19-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="90c19-107">[v] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) hodnotu, která určuje typ deklarativní zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="90c19-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="90c19-108">[v] Oprávnění objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="90c19-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="90c19-109">[v] Velikost v bajtech z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="90c19-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="90c19-110">[out] Token vrácený oprávnění.</span><span class="sxs-lookup"><span data-stu-id="90c19-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90c19-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90c19-111">Requirements</span></span>  
 <span data-ttu-id="90c19-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90c19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90c19-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90c19-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90c19-114">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90c19-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90c19-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90c19-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c19-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="90c19-116">See Also</span></span>  
 [<span data-ttu-id="90c19-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90c19-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="90c19-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90c19-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
