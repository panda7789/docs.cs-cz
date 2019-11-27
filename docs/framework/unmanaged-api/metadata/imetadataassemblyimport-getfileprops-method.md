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
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="e72bf-102">IMetaDataAssemblyImport::GetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e72bf-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="e72bf-103">Získá vlastnosti souboru se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="e72bf-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e72bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e72bf-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e72bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e72bf-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="e72bf-106">pro Token metadat `mdFile`, který představuje soubor, pro který se mají získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e72bf-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="e72bf-107">mimo Jednoduchý název souboru.</span><span class="sxs-lookup"><span data-stu-id="e72bf-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e72bf-108">pro Velikost v rámci velkých znaků `szName`.</span><span class="sxs-lookup"><span data-stu-id="e72bf-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="e72bf-109">mimo Počet znaků, které jsou ve skutečnosti vraceny `szName`.</span><span class="sxs-lookup"><span data-stu-id="e72bf-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="e72bf-110">mimo Ukazatel na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="e72bf-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="e72bf-111">Toto je hodnota hash pomocí algoritmu SHA-1 souboru.</span><span class="sxs-lookup"><span data-stu-id="e72bf-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="e72bf-112">mimo Počet velkých znaků v vrácené hodnotě hash.</span><span class="sxs-lookup"><span data-stu-id="e72bf-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="e72bf-113">mimo Ukazatel na příznaky, které popisují metadata použitá pro soubor.</span><span class="sxs-lookup"><span data-stu-id="e72bf-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="e72bf-114">Hodnota příznaků je kombinací jedné nebo více hodnot [CorFileFlags –](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="e72bf-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e72bf-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e72bf-115">Requirements</span></span>  
 <span data-ttu-id="e72bf-116">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e72bf-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e72bf-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e72bf-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e72bf-118">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e72bf-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e72bf-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e72bf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e72bf-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e72bf-120">See also</span></span>

- [<span data-ttu-id="e72bf-121">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e72bf-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
