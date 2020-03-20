---
title: IMetaDataAssemblyEmit::SetFileProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 25baa6ffda3d50915cc7898275d6a557c1b3e947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176029"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="7241c-102">IMetaDataAssemblyEmit::SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7241c-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="7241c-103">Upraví zadanou `File` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="7241c-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7241c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7241c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7241c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7241c-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="7241c-106">[v] Token metadat, který určuje `File` strukturu metadat, která má být změněna.</span><span class="sxs-lookup"><span data-stu-id="7241c-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="7241c-107">[v] Ukazatel na data hash přidružená k souboru.</span><span class="sxs-lookup"><span data-stu-id="7241c-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="7241c-108">[v] Velikost v bajtů `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="7241c-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="7241c-109">[v] Bitová kombinace hodnot [CorFileFlags,](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) které určují různé atributy souboru.</span><span class="sxs-lookup"><span data-stu-id="7241c-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7241c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7241c-110">Remarks</span></span>  
 <span data-ttu-id="7241c-111">Chcete-li `File` vytvořit strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::DefineFile.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)</span><span class="sxs-lookup"><span data-stu-id="7241c-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7241c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7241c-112">Requirements</span></span>  
 <span data-ttu-id="7241c-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7241c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7241c-114">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="7241c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7241c-115">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7241c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7241c-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7241c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7241c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7241c-117">See also</span></span>

- [<span data-ttu-id="7241c-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7241c-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
