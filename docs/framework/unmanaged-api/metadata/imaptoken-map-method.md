---
title: IMapToken::Map – metoda
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2633bfadaabf208a2b86fda83375c3a136b93b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448169"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="d9319-102">IMapToken::Map – metoda</span><span class="sxs-lookup"><span data-stu-id="d9319-102">IMapToken::Map Method</span></span>
<span data-ttu-id="d9319-103">Mapuje vztah mezi sestavení pomocí metadat podpisy.</span><span class="sxs-lookup"><span data-stu-id="d9319-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9319-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9319-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9319-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9319-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="d9319-106">[v] Metadata token, který představuje objekt importované kódu.</span><span class="sxs-lookup"><span data-stu-id="d9319-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="d9319-107">[v] Metadata token, který představuje objekt emitovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="d9319-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9319-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9319-108">Remarks</span></span>  
 <span data-ttu-id="d9319-109">Když tokenu znovu namapovat dojde během sloučení, původní token má obor v oboru metadata importované (zdroj) a nový token má obor v oboru metadata emitovaného (cíl).</span><span class="sxs-lookup"><span data-stu-id="d9319-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9319-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9319-110">Requirements</span></span>  
 <span data-ttu-id="d9319-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9319-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9319-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d9319-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9319-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9319-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9319-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9319-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9319-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9319-115">See Also</span></span>  
 [<span data-ttu-id="d9319-116">IMapToken – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9319-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
