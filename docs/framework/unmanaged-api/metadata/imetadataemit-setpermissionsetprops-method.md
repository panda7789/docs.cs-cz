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
ms.openlocfilehash: 1e6ee1f2f497ef30a5390e7afac55c54705248ed
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007803"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="bacf6-102">IMetaDataEmit::SetPermissionSetProps – metoda</span><span class="sxs-lookup"><span data-stu-id="bacf6-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="bacf6-103">Nastaví nebo aktualizuje funkce signatury metadat sady oprávnění definované předchozím voláním [IMetaDataEmit::D efinepermissionset](imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="bacf6-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bacf6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bacf6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bacf6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bacf6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bacf6-106">pro Token metadat, který představuje objekt, který má být upraven.</span><span class="sxs-lookup"><span data-stu-id="bacf6-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="bacf6-107">pro Hodnota [CorDeclSecurity –](cordeclsecurity-enumeration.md) , která určuje typ deklarativního zabezpečení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="bacf6-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="bacf6-108">pro Objekt BLOB oprávnění</span><span class="sxs-lookup"><span data-stu-id="bacf6-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="bacf6-109">pro Velikost v bajtech `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="bacf6-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="bacf6-110">mimo `mdPermission`Token metadat, který představuje aktualizovaná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="bacf6-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bacf6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bacf6-111">Requirements</span></span>  
 <span data-ttu-id="bacf6-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bacf6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bacf6-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bacf6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bacf6-114">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="bacf6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bacf6-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bacf6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bacf6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bacf6-116">See also</span></span>

- [<span data-ttu-id="bacf6-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bacf6-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="bacf6-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bacf6-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
