---
title: IMetaDataImport::EnumPermissionSets – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: e628cf5dab8006b0df0ab6c60dc995cd0c6bb29d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175444"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="3e332-102">IMetaDataImport::EnumPermissionSets – metoda</span><span class="sxs-lookup"><span data-stu-id="3e332-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="3e332-103">Vyjmenovává oprávnění pro objekty v zadaném oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="3e332-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e332-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e332-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e332-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e332-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3e332-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="3e332-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3e332-107">To musí být NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="3e332-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="3e332-108">[v] Token metadat, který omezuje rozsah hledání nebo NULL prohledat co nejširší obor.</span><span class="sxs-lookup"><span data-stu-id="3e332-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="3e332-109">[v] Příznaky představující <xref:System.Security.Permissions.SecurityAction> hodnoty, které `rPermission`mají být zahrnuty do , nebo nula vrátit všechny akce.</span><span class="sxs-lookup"><span data-stu-id="3e332-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="3e332-110">[out] Pole používané k ukládání tokenů oprávnění.</span><span class="sxs-lookup"><span data-stu-id="3e332-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3e332-111">[v] Maximální velikost `rPermission` pole.</span><span class="sxs-lookup"><span data-stu-id="3e332-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3e332-112">[out] Počet tokenů oprávnění vrácených v `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="3e332-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e332-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e332-113">Return Value</span></span>  
  
|<span data-ttu-id="3e332-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e332-114">HRESULT</span></span>|<span data-ttu-id="3e332-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3e332-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3e332-116">`EnumPermissionSets`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3e332-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3e332-117">Neexistují žádné tokeny výčet.</span><span class="sxs-lookup"><span data-stu-id="3e332-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="3e332-118">V tom `pcTokens` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="3e332-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e332-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e332-119">Requirements</span></span>  
 <span data-ttu-id="3e332-120">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e332-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e332-121">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="3e332-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e332-122">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e332-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e332-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e332-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e332-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e332-124">See also</span></span>

- [<span data-ttu-id="3e332-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e332-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3e332-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e332-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
