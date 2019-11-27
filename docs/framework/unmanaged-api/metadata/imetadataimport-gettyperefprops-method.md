---
title: IMetaDataImport::GetTypeRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 6ea7605e062eb77e0488b3a9561c4d83be16fa7d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436707"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="8b157-102">IMetaDataImport::GetTypeRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="8b157-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="8b157-103">Získá metadata přidružená k <xref:System.Type>, na kterou odkazuje zadaný token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="8b157-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b157-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b157-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b157-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b157-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="8b157-106">pro Token TypeRef, který představuje typ, pro který se mají vracet metadata</span><span class="sxs-lookup"><span data-stu-id="8b157-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="8b157-107">mimo Ukazatel na obor, ve kterém je odkaz proveden.</span><span class="sxs-lookup"><span data-stu-id="8b157-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="8b157-108">Tato hodnota je AssemblyRef nebo odkaz ModuleRef token.</span><span class="sxs-lookup"><span data-stu-id="8b157-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="8b157-109">mimo Vyrovnávací paměť obsahující název typu.</span><span class="sxs-lookup"><span data-stu-id="8b157-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8b157-110">pro Požadovaná velikost v různých znacích `szName`.</span><span class="sxs-lookup"><span data-stu-id="8b157-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8b157-111">mimo Vrácená velikost v různých znacích `szName`.</span><span class="sxs-lookup"><span data-stu-id="8b157-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b157-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b157-112">Requirements</span></span>  
 <span data-ttu-id="8b157-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b157-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b157-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8b157-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b157-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8b157-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b157-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b157-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b157-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b157-117">See also</span></span>

- [<span data-ttu-id="8b157-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b157-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8b157-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b157-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
