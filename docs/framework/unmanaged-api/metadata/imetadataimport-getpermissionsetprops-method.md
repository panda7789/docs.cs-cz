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
ms.openlocfilehash: 5faf1a6ae89045b2ef17fab789ee6e5bf23eecf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175340"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="cdafb-102">IMetaDataImport::GetPermissionSetProps – metoda</span><span class="sxs-lookup"><span data-stu-id="cdafb-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="cdafb-103">Získá metadata spojená <xref:System.Security.PermissionSet?displayProperty=nameWithType> s reprezentované zadaným tokenem oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cdafb-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdafb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdafb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdafb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdafb-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="cdafb-106">[v] Token metadat oprávnění, který představuje sadu oprávnění pro získání vlastností metadat.</span><span class="sxs-lookup"><span data-stu-id="cdafb-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="cdafb-107">[out] Ukazatel na sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cdafb-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="cdafb-108">[out] Ukazatel na podpis binárních metadat sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cdafb-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="cdafb-109">[out] Velikost v bajtů `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="cdafb-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdafb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdafb-110">Requirements</span></span>  
 <span data-ttu-id="cdafb-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdafb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdafb-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="cdafb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cdafb-113">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cdafb-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cdafb-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdafb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdafb-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdafb-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="cdafb-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cdafb-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cdafb-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cdafb-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
