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
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008063"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="e0933-102">IMetaDataAssemblyEmit::SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e0933-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="e0933-103">Upraví zadanou `File` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="e0933-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0933-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0933-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0933-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0933-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="e0933-106">pro Token metadat, který určuje `File` strukturu metadat, která má být upravena.</span><span class="sxs-lookup"><span data-stu-id="e0933-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="e0933-107">pro Ukazatel na data algoritmu hash přidružená k souboru.</span><span class="sxs-lookup"><span data-stu-id="e0933-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="e0933-108">pro Velikost v bajtech `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="e0933-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="e0933-109">pro Bitová kombinace hodnot [CorFileFlags –](corfileflags-enumeration.md) , které určují různé atributy souboru.</span><span class="sxs-lookup"><span data-stu-id="e0933-109">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0933-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0933-110">Remarks</span></span>  
 <span data-ttu-id="e0933-111">Chcete-li vytvořit `File` strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::D efinefile](imetadataassemblyemit-definefile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e0933-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0933-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0933-112">Requirements</span></span>  
 <span data-ttu-id="e0933-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0933-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0933-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e0933-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0933-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e0933-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0933-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0933-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0933-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0933-117">See also</span></span>

- [<span data-ttu-id="e0933-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0933-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
