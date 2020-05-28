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
ms.openlocfilehash: 027694cee1b3e4d990796ba31300918f6d859679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008193"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="6f73d-102">IMapToken::Map – metoda</span><span class="sxs-lookup"><span data-stu-id="6f73d-102">IMapToken::Map Method</span></span>
<span data-ttu-id="6f73d-103">Mapuje vztah mezi sestaveními pomocí podpisů metadat.</span><span class="sxs-lookup"><span data-stu-id="6f73d-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f73d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f73d-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f73d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f73d-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="6f73d-106">pro Token metadat, který reprezentuje objekt importovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6f73d-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="6f73d-107">pro Token metadat, který reprezentuje objekt emitovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6f73d-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f73d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f73d-108">Remarks</span></span>  
 <span data-ttu-id="6f73d-109">Když dojde ke změně tokenu během sloučení, původní token se zaznamená v importovaném (zdrojovém) oboru metadat a nový token je vymezen v oboru metadat emited (Targeting).</span><span class="sxs-lookup"><span data-stu-id="6f73d-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f73d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f73d-110">Requirements</span></span>  
 <span data-ttu-id="6f73d-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f73d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f73d-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6f73d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f73d-113">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="6f73d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f73d-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f73d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f73d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f73d-115">See also</span></span>

- [<span data-ttu-id="6f73d-116">IMapToken – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f73d-116">IMapToken Interface</span></span>](imaptoken-interface.md)
