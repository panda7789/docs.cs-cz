---
title: "IMetaDataAssemblyImport::GetAssemblyRefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9159352c4f7f338c6b9b82ea579ad3cb36c19007
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="1a2a2-102">IMetaDataAssemblyImport::GetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="1a2a2-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="1a2a2-103">Získá sadu vlastností pro odkaz na sestavení s podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a2a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a2a2-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="1a2a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a2a2-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="1a2a2-106">[v] `mdAssemblyRef` Metadata token, který představuje odkaz na sestavení, pro které chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="1a2a2-107">[out] Ukazatel na veřejný klíč, nebo token pro metadata.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="1a2a2-108">[out] Počet bajtů vrácených veřejný klíč, nebo token.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="1a2a2-109">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1a2a2-110">[v] Velikost v široké znaků, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1a2a2-111">[out] Ukazatel na počet široké znaků ve skutečnosti, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="1a2a2-112">[out] Ukazatel na assemblymetadata – struktura, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="1a2a2-113">[out] Ukazatel na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="1a2a2-114">Toto je hodnota hash, pomocí algoritmu SHA-1 z `PublicKey` vlastnost sestavení odkazováno, pokud arfFullOriginator příznak [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) výčtu nastavena.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="1a2a2-115">[out] Počet široké znaků v hodnotě vrácené hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="1a2a2-116">[out] Ukazatel na příznaky, které popisují metadata použijí k sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="1a2a2-117">Hodnota příznaky je kombinací jednoho nebo více [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a2a2-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1a2a2-118">Return Value</span></span>  
 <span data-ttu-id="1a2a2-119">Tato metoda vrátí S_OK Pokud neproběhne úspěšně. jinak vrátí jeden z definovaných v záhlaví souboru Winerror.h kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="1a2a2-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a2a2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a2a2-120">Requirements</span></span>  
 <span data-ttu-id="1a2a2-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a2a2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a2a2-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a2a2-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a2a2-123">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a2a2-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a2a2-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a2a2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a2a2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a2a2-125">See Also</span></span>  
 [<span data-ttu-id="1a2a2-126">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a2a2-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
