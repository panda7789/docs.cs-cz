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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 990910b8b30e9794550d71cf9eaf8cd53639f696
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492241"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="e2671-102">IMetaDataImport::EnumPermissionSets – metoda</span><span class="sxs-lookup"><span data-stu-id="e2671-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="e2671-103">Vytvoří výčet oprávnění pro objekty v oboru Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="e2671-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2671-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2671-104">Syntax</span></span>  
  
```  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2671-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2671-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e2671-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e2671-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e2671-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="e2671-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="e2671-108">[in] Token metadat, který omezuje obor vyhledávání, nebo hodnota NULL pro hledání oboru nejširší možné.</span><span class="sxs-lookup"><span data-stu-id="e2671-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="e2671-109">[in] Příznaky představující <xref:System.Security.Permissions.SecurityAction> hodnoty pro zahrnutí `rPermission`, nebo nula, která vrátí všechny akce.</span><span class="sxs-lookup"><span data-stu-id="e2671-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="e2671-110">[out] Pole pro ukládání tokenů oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e2671-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e2671-111">[in] Maximální velikost `rPermission` pole.</span><span class="sxs-lookup"><span data-stu-id="e2671-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e2671-112">[out] Počet tokenů oprávnění vrácené v `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="e2671-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2671-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e2671-113">Return Value</span></span>  
  
|<span data-ttu-id="e2671-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2671-114">HRESULT</span></span>|<span data-ttu-id="e2671-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e2671-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e2671-116">`EnumPermissionSets` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e2671-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e2671-117">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="e2671-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="e2671-118">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="e2671-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2671-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2671-119">Requirements</span></span>  
 <span data-ttu-id="e2671-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2671-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2671-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e2671-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2671-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e2671-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2671-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2671-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2671-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2671-124">See also</span></span>
- [<span data-ttu-id="e2671-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2671-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e2671-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2671-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
