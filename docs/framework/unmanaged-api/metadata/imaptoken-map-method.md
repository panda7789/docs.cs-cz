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
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176068"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="ffeaa-102">IMapToken::Map – metoda</span><span class="sxs-lookup"><span data-stu-id="ffeaa-102">IMapToken::Map Method</span></span>
<span data-ttu-id="ffeaa-103">Mapuje vztah mezi sestaveními pomocí podpisů metadat.</span><span class="sxs-lookup"><span data-stu-id="ffeaa-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffeaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffeaa-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffeaa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffeaa-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="ffeaa-106">[v] Token metadat, který představuje importovaný objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="ffeaa-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="ffeaa-107">[v] Token metadat, který představuje objekt emitovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ffeaa-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffeaa-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ffeaa-108">Remarks</span></span>  
 <span data-ttu-id="ffeaa-109">Když dojde k opětovnému mapování tokenu během sloučení, původní token je vymezen v oboru importovaného (zdrojového) metadat a nový token je vymezen v oboru emitovaných (cílových) metadat.</span><span class="sxs-lookup"><span data-stu-id="ffeaa-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffeaa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffeaa-110">Requirements</span></span>  
 <span data-ttu-id="ffeaa-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffeaa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffeaa-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="ffeaa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffeaa-113">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffeaa-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ffeaa-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffeaa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffeaa-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffeaa-115">See also</span></span>

- [<span data-ttu-id="ffeaa-116">IMapToken – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffeaa-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
