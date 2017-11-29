---
title: "IMetaDataEmit::DefinePermissionSet – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefinePermissionSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a503f22710f392ecbb0ae2704d2c2950a858c30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="0ab6a-102">IMetaDataEmit::DefinePermissionSet – metoda</span><span class="sxs-lookup"><span data-stu-id="0ab6a-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="0ab6a-103">Vytvoří definici oprávnění nastavit podpisem Zadaná metadata a získá token pro tuto definici sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ab6a-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ab6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ab6a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0ab6a-106">[v] Objekt, který má být doplněný o atribut.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="0ab6a-107">[v] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) hodnotu, která určuje typ deklarativní zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="0ab6a-108">[v] Oprávnění objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="0ab6a-109">[v] Velikost v bajtech z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="0ab6a-110">[out] Token vrácený oprávnění.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ab6a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ab6a-111">Requirements</span></span>  
 <span data-ttu-id="0ab6a-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ab6a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ab6a-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ab6a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ab6a-114">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ab6a-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ab6a-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ab6a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab6a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ab6a-116">See Also</span></span>  
 [<span data-ttu-id="0ab6a-117">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ab6a-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="0ab6a-118">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ab6a-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
