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
ms.openlocfilehash: 8057406552525be19f8e6457de9faf841edc6e68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429498"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="4577e-102">IAssemblyCacheItem::CreateStream – metoda</span><span class="sxs-lookup"><span data-stu-id="4577e-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="4577e-103">Vytvoří datový proud se zadaným názvem a formát.</span><span class="sxs-lookup"><span data-stu-id="4577e-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4577e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4577e-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="4577e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4577e-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="4577e-106">[v] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="4577e-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="4577e-107">[v] Název datového proudu, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="4577e-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="4577e-108">[v] Formát souboru pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="4577e-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="4577e-109">[v] Specifické pro formát příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="4577e-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="4577e-110">[out] Ukazatel na adresu vrácený [IStream on Request](https://msdn.microsoft.com/library/aa380034.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="4577e-110">[out] A pointer to the address of the returned [IStream](https://msdn.microsoft.com/library/aa380034.aspx) instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="4577e-111">[v, optional] Maximální velikost datového proudu odkazuje `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="4577e-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4577e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4577e-112">Requirements</span></span>  
 <span data-ttu-id="4577e-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4577e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4577e-114">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4577e-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4577e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4577e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4577e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4577e-116">See Also</span></span>  
 [<span data-ttu-id="4577e-117">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4577e-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
