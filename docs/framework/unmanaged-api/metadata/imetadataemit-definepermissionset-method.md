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
ms.openlocfilehash: 4e11a52c977de7796043868e80c147d8cfd1f506
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431569"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="b9ce6-102">IMetaDataEmit::DefinePermissionSet – metoda</span><span class="sxs-lookup"><span data-stu-id="b9ce6-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="b9ce6-103">Vytvoří definici sady oprávnění se zadaným podpisem metadat a získá token do této definice sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b9ce6-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ce6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9ce6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9ce6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9ce6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b9ce6-106">pro Objekt, který má být upraven.</span><span class="sxs-lookup"><span data-stu-id="b9ce6-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="b9ce6-107">pro Hodnota [CorDeclSecurity –](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) , která určuje typ deklarativního zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="b9ce6-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="b9ce6-108">pro Objekt BLOB oprávnění</span><span class="sxs-lookup"><span data-stu-id="b9ce6-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="b9ce6-109">pro Velikost `pvPermission`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b9ce6-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="b9ce6-110">mimo Vrácený token oprávnění</span><span class="sxs-lookup"><span data-stu-id="b9ce6-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9ce6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9ce6-111">Requirements</span></span>  
 <span data-ttu-id="b9ce6-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9ce6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ce6-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b9ce6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9ce6-114">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="b9ce6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9ce6-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9ce6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ce6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9ce6-116">See also</span></span>

- [<span data-ttu-id="b9ce6-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9ce6-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b9ce6-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9ce6-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
