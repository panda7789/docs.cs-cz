---
title: IMetaDataEmit::DefinePinvokeMap – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: 9d4ea16a212ac5f0120d63510f07eaee69af739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431484"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="a168c-102">IMetaDataEmit::DefinePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="a168c-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="a168c-103">Nastaví funkce signatury PInvoke metody, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="a168c-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a168c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a168c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a168c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a168c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a168c-106">pro Token pro cílovou metodu</span><span class="sxs-lookup"><span data-stu-id="a168c-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="a168c-107">pro Příznaky používané v PInvoke k mapování.</span><span class="sxs-lookup"><span data-stu-id="a168c-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="a168c-108">pro Název cílové metody exportu v nespravované knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="a168c-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="a168c-109">pro Token pro cílovou nativní knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="a168c-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a168c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a168c-110">Requirements</span></span>  
 <span data-ttu-id="a168c-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a168c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a168c-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a168c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a168c-113">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="a168c-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a168c-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a168c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a168c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a168c-115">See also</span></span>

- [<span data-ttu-id="a168c-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a168c-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a168c-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a168c-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
