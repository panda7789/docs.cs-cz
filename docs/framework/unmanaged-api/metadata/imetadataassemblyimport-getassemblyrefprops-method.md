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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175964"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="d6121-102">IMetaDataAssemblyImport::GetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d6121-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="d6121-103">Získá sadu vlastností pro odkaz na sestavení s zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="d6121-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6121-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6121-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d6121-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6121-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="d6121-106">[v] Token `mdAssemblyRef` metadat, který představuje odkaz na sestavení, pro které chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6121-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="d6121-107">[out] Ukazatel na veřejný klíč nebo token metadat.</span><span class="sxs-lookup"><span data-stu-id="d6121-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="d6121-108">[out] Počet bajtů ve vráceném veřejném klíči nebo tokenu.</span><span class="sxs-lookup"><span data-stu-id="d6121-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="d6121-109">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6121-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d6121-110">[v] Velikost , v širokých `szName`znaků, .</span><span class="sxs-lookup"><span data-stu-id="d6121-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="d6121-111">[out] Ukazatel na počet širokých znaků skutečně `szName`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="d6121-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="d6121-112">[out] Ukazatel na strukturu ASSEMBLYMETADATA, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6121-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="d6121-113">[out] Ukazatel na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="d6121-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="d6121-114">Toto je algoritmus hash pomocí algoritmu `PublicKey` SHA-1 vlastnosti naváděného sestavení, pokud není nastaven příznak arfFullOriginator výčtu [AssemblyRefFlags.](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="d6121-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="d6121-115">[out] Počet širokých znaků ve vrácené hodnotě hash.</span><span class="sxs-lookup"><span data-stu-id="d6121-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="d6121-116">[out] Ukazatel na příznaky, které popisují metadata použitá v sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6121-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="d6121-117">Hodnota příznaků je kombinací jedné nebo více hodnot [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="d6121-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6121-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6121-118">Return Value</span></span>  
 <span data-ttu-id="d6121-119">Tato metoda vrátí S_OK pokud je úspěšná; v opačném případě vrátí jeden z kódů chyb definovaných v souboru hlavičky Winerror.h.</span><span class="sxs-lookup"><span data-stu-id="d6121-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6121-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6121-120">Requirements</span></span>  
 <span data-ttu-id="d6121-121">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6121-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6121-122">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="d6121-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6121-123">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6121-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6121-124">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6121-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6121-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6121-125">See also</span></span>

- [<span data-ttu-id="d6121-126">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6121-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
