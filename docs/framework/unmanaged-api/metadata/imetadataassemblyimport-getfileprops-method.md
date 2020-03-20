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
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175977"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="3584c-102">IMetaDataAssemblyImport::GetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="3584c-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="3584c-103">Získá vlastnosti souboru se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="3584c-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3584c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3584c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3584c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3584c-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="3584c-106">[v] Token `mdFile` metadat, který představuje soubor, pro který chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3584c-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="3584c-107">[out] Jednoduchý název souboru.</span><span class="sxs-lookup"><span data-stu-id="3584c-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3584c-108">[v] Velikost , v širokých `szName`znaků, .</span><span class="sxs-lookup"><span data-stu-id="3584c-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="3584c-109">[out] Počet širokých znaků skutečně `szName`vrátil v .</span><span class="sxs-lookup"><span data-stu-id="3584c-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="3584c-110">[out] Ukazatel na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="3584c-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="3584c-111">Toto je algoritmus hash pomocí algoritmu SHA-1 souboru.</span><span class="sxs-lookup"><span data-stu-id="3584c-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="3584c-112">[out] Počet širokých znaků ve vrácené hodnotě hash.</span><span class="sxs-lookup"><span data-stu-id="3584c-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="3584c-113">[out] Ukazatel na příznaky, které popisují metadata použitá v souboru.</span><span class="sxs-lookup"><span data-stu-id="3584c-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="3584c-114">Hodnota příznaky je kombinací jedné nebo více hodnot [CorFileFlags.](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="3584c-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3584c-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3584c-115">Requirements</span></span>  
 <span data-ttu-id="3584c-116">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3584c-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3584c-117">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="3584c-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3584c-118">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3584c-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3584c-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3584c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3584c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3584c-120">See also</span></span>

- [<span data-ttu-id="3584c-121">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3584c-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
