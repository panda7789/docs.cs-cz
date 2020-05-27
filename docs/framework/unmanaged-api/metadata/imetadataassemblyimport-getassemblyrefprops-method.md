---
title: IMetaDataAssemblyImport::GetAssemblyRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 2858e924ab6effe192955ce53dad9d333d2d244d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009064"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="c2048-102">IMetaDataAssemblyImport::GetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c2048-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="c2048-103">Získá sadu vlastností pro odkaz na sestavení se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="c2048-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2048-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2048-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2048-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2048-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="c2048-106">pro `mdAssemblyRef`Token metadat, který představuje odkaz na sestavení, pro který se mají získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2048-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="c2048-107">mimo Ukazatel na veřejný klíč nebo token metadat.</span><span class="sxs-lookup"><span data-stu-id="c2048-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="c2048-108">mimo Počet bajtů v vráceném veřejném klíči nebo tokenu.</span><span class="sxs-lookup"><span data-stu-id="c2048-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="c2048-109">mimo Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="c2048-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c2048-110">pro Velikost ve velkých znakech `szName` .</span><span class="sxs-lookup"><span data-stu-id="c2048-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c2048-111">mimo Ukazatel na počet velkých znaků, které se ve skutečnosti vrátily `szName` .</span><span class="sxs-lookup"><span data-stu-id="c2048-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c2048-112">mimo Ukazatel na strukturu AssemblyMetadata –, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="c2048-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="c2048-113">mimo Ukazatel na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="c2048-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="c2048-114">Toto je hodnota hash pomocí algoritmu SHA-1 `PublicKey` Vlastnosti odkazovaného sestavení, pokud není nastaven příznak arfFullOriginator výčtu [AssemblyRefFlags –](assemblyrefflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c2048-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="c2048-115">mimo Počet velkých znaků v vrácené hodnotě hash.</span><span class="sxs-lookup"><span data-stu-id="c2048-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="c2048-116">mimo Ukazatel na příznaky, které popisují metadata použitá pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="c2048-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="c2048-117">Hodnota příznaků je kombinací jedné nebo více hodnot [CorAssemblyFlags –](corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c2048-117">The flags value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2048-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c2048-118">Return Value</span></span>  
 <span data-ttu-id="c2048-119">Tato metoda vrátí S_OK, pokud je úspěšná; v opačném případě vrátí jeden z kódů chyb definovaných v souboru hlaviček Winerror. h.</span><span class="sxs-lookup"><span data-stu-id="c2048-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2048-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2048-120">Requirements</span></span>  
 <span data-ttu-id="c2048-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2048-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2048-122">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c2048-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2048-123">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="c2048-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2048-124">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2048-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2048-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2048-125">See also</span></span>

- [<span data-ttu-id="c2048-126">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2048-126">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
