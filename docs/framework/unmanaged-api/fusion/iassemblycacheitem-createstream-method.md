---
title: IAssemblyCacheItem::CreateStream – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b3242e8ae29b9d21dc50d3ea0476967e9746f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031372"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="b9bec-102">IAssemblyCacheItem::CreateStream – metoda</span><span class="sxs-lookup"><span data-stu-id="b9bec-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="b9bec-103">Vytvoří datový proud se zadaným názvem a formát.</span><span class="sxs-lookup"><span data-stu-id="b9bec-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9bec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9bec-104">Syntax</span></span>  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9bec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9bec-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b9bec-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b9bec-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="b9bec-107">[in] Název datového proudu, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="b9bec-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="b9bec-108">[in] Formát souboru, který má být datovým proudem.</span><span class="sxs-lookup"><span data-stu-id="b9bec-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="b9bec-109">[in] Příznaky formátu konkrétní definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b9bec-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="b9bec-110">[out] Ukazatel na adresu vráceného [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span><span class="sxs-lookup"><span data-stu-id="b9bec-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="b9bec-111">[in, volitelné] Maximální velikost datového proudu odkazuje `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="b9bec-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9bec-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9bec-112">Requirements</span></span>  
 <span data-ttu-id="b9bec-113">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9bec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9bec-114">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b9bec-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b9bec-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9bec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9bec-116">See Also</span></span>  
 [<span data-ttu-id="b9bec-117">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9bec-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
