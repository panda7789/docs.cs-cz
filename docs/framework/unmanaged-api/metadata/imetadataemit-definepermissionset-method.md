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
ms.openlocfilehash: a069e2f4ec5d4114e9504fa5a58c5066fdfd7249
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008037"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="00023-102">IMetaDataEmit::DefinePermissionSet – metoda</span><span class="sxs-lookup"><span data-stu-id="00023-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="00023-103">Vytvoří definici sady oprávnění se zadaným podpisem metadat a získá token do této definice sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="00023-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00023-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00023-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00023-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00023-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="00023-106">pro Objekt, který má být upraven.</span><span class="sxs-lookup"><span data-stu-id="00023-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="00023-107">pro Hodnota [CorDeclSecurity –](cordeclsecurity-enumeration.md) , která určuje typ deklarativního zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="00023-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="00023-108">pro Objekt BLOB oprávnění</span><span class="sxs-lookup"><span data-stu-id="00023-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="00023-109">pro Velikost v bajtech `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="00023-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="00023-110">mimo Vrácený token oprávnění</span><span class="sxs-lookup"><span data-stu-id="00023-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00023-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00023-111">Requirements</span></span>  
 <span data-ttu-id="00023-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00023-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00023-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="00023-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00023-114">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="00023-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00023-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00023-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00023-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="00023-116">See also</span></span>

- [<span data-ttu-id="00023-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00023-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="00023-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00023-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
