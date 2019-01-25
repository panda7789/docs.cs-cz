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
ms.openlocfilehash: 31c18061ad5f21e26665cd0d6883b0eb26afd1d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557472"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="03166-102">IMapToken::Map – metoda</span><span class="sxs-lookup"><span data-stu-id="03166-102">IMapToken::Map Method</span></span>
<span data-ttu-id="03166-103">Mapuje vztah mezi sestaveními, používání metadat podpisů.</span><span class="sxs-lookup"><span data-stu-id="03166-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03166-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03166-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03166-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03166-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="03166-106">[in] Token metadat, který představuje kód importovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="03166-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="03166-107">[in] Token metadat, který představuje objekt emitovaný kód.</span><span class="sxs-lookup"><span data-stu-id="03166-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03166-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03166-108">Remarks</span></span>  
 <span data-ttu-id="03166-109">Když tokenu přemapovat spadá sloučení, původní token má obor v oboru metadata importované (zdroj) a nový token působí v rámci metadata emitovaný (cíl).</span><span class="sxs-lookup"><span data-stu-id="03166-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03166-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03166-110">Requirements</span></span>  
 <span data-ttu-id="03166-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03166-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03166-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03166-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03166-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03166-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03166-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03166-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03166-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03166-115">See also</span></span>
- [<span data-ttu-id="03166-116">IMapToken – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03166-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
