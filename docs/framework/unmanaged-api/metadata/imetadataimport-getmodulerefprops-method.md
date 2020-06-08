---
title: IMetaDataImport::GetModuleRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: f1784c9f3085ce188f9e540887dd02064f8448f3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503572"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="2520d-102">IMetaDataImport::GetModuleRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2520d-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="2520d-103">Získá název modulu, na který odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="2520d-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2520d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2520d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2520d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2520d-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="2520d-106">pro Token metadat Odkaz ModuleRef, který odkazuje na modul, aby získal informace o metadatech pro.</span><span class="sxs-lookup"><span data-stu-id="2520d-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="2520d-107">mimo Vyrovnávací paměť pro uložení názvu modulu.</span><span class="sxs-lookup"><span data-stu-id="2520d-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2520d-108">pro Požadovaná velikost `szName` v rámci velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="2520d-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2520d-109">mimo Vrácená velikost `szName` v rámci velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="2520d-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2520d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2520d-110">Requirements</span></span>  
 <span data-ttu-id="2520d-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2520d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2520d-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2520d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2520d-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2520d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2520d-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2520d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2520d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2520d-115">See also</span></span>

- [<span data-ttu-id="2520d-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2520d-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2520d-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2520d-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
