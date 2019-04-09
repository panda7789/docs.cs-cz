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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da38c04f5d67dc0220b1828ba0e5cdeb84346bb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137940"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="03069-102">IMetaDataAssemblyImport::GetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="03069-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="03069-103">Získá vlastnosti souboru s podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="03069-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03069-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03069-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="03069-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03069-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="03069-106">[in] `mdFile` Token metadat, který představuje soubor, pro které chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="03069-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="03069-107">[out] Jednoduchý název souboru.</span><span class="sxs-lookup"><span data-stu-id="03069-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="03069-108">[in] Velikost v široké znaky z `szName`.</span><span class="sxs-lookup"><span data-stu-id="03069-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="03069-109">[out] Počet skutečně vrácených v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="03069-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="03069-110">[out] Ukazatel na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="03069-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="03069-111">Toto je hodnota hash pomocí algoritmu SHA-1 souboru.</span><span class="sxs-lookup"><span data-stu-id="03069-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="03069-112">[out] Počet široké znaky v hodnotě vrácené hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="03069-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="03069-113">[out] Ukazatel na příznaky, které popisují metadata u souboru.</span><span class="sxs-lookup"><span data-stu-id="03069-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="03069-114">Hodnota příznaků je kombinace jedné nebo více [corfileflags –](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="03069-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03069-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03069-115">Requirements</span></span>  
 <span data-ttu-id="03069-116">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03069-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03069-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03069-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03069-118">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03069-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="03069-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="03069-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03069-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03069-120">See also</span></span>

- [<span data-ttu-id="03069-121">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03069-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
