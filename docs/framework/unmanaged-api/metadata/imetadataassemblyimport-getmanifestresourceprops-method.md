---
title: IMetaDataAssemblyImport::GetManifestResourceProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009025"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="50254-102">IMetaDataAssemblyImport::GetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="50254-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="50254-103">Získá sadu vlastností prostředku manifestu se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="50254-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50254-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50254-104">Syntax</span></span>  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50254-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50254-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="50254-106">pro `mdManifestResource`Token, který představuje prostředek, pro který chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="50254-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="50254-107">mimo Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="50254-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="50254-108">pro Velikost ve velkých znakech `szName` .</span><span class="sxs-lookup"><span data-stu-id="50254-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="50254-109">mimo Ukazatel na počet velkých znaků, které se ve skutečnosti vrátily `szName` .</span><span class="sxs-lookup"><span data-stu-id="50254-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="50254-110">mimo Ukazatel na `mdFile` token nebo `mdAssemblyRef` token, který představuje soubor nebo sestavení, v uvedeném pořadí, které obsahuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="50254-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="50254-111">mimo Ukazatel na hodnotu, která určuje posun na začátek prostředku v rámci souboru.</span><span class="sxs-lookup"><span data-stu-id="50254-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="50254-112">mimo Ukazatel na příznaky, které popisují metadata použitá u prostředku.</span><span class="sxs-lookup"><span data-stu-id="50254-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="50254-113">Hodnota příznaků je kombinací jedné nebo více hodnot [CorManifestResourceFlags –](cormanifestresourceflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="50254-113">The flags value is a combination of one or more [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50254-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50254-114">Requirements</span></span>  
 <span data-ttu-id="50254-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50254-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50254-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="50254-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50254-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="50254-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50254-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50254-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50254-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="50254-119">See also</span></span>

- [<span data-ttu-id="50254-120">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50254-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
