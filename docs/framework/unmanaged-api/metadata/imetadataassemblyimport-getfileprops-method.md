---
title: IMetaDataAssemblyImport::GetFileProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: beb697d80417b937876a0887e4376341185a47d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447208"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="617e4-102">IMetaDataAssemblyImport::GetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="617e4-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="617e4-103">Gets the properties of the file with the specified metadata signature.</span><span class="sxs-lookup"><span data-stu-id="617e4-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="617e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="617e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="617e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="617e4-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="617e4-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span><span class="sxs-lookup"><span data-stu-id="617e4-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="617e4-107">[out] The simple name of the file.</span><span class="sxs-lookup"><span data-stu-id="617e4-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="617e4-108">[in] The size, in wide chars, of `szName`.</span><span class="sxs-lookup"><span data-stu-id="617e4-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="617e4-109">[out] The number of wide chars actually returned in `szName`.</span><span class="sxs-lookup"><span data-stu-id="617e4-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="617e4-110">[out] A pointer to the hash value.</span><span class="sxs-lookup"><span data-stu-id="617e4-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="617e4-111">This is the hash, using the SHA-1 algorithm, of the file.</span><span class="sxs-lookup"><span data-stu-id="617e4-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="617e4-112">[out] The number of wide chars in the returned hash value.</span><span class="sxs-lookup"><span data-stu-id="617e4-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="617e4-113">[out] A pointer to the flags that describe the metadata applied to a file.</span><span class="sxs-lookup"><span data-stu-id="617e4-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="617e4-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span><span class="sxs-lookup"><span data-stu-id="617e4-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="617e4-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="617e4-115">Requirements</span></span>  
 <span data-ttu-id="617e4-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="617e4-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="617e4-117">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="617e4-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="617e4-118">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="617e4-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="617e4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="617e4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617e4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="617e4-120">See also</span></span>

- [<span data-ttu-id="617e4-121">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="617e4-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
