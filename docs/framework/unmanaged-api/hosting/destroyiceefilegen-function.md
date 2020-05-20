---
title: DestroyICeeFileGen – funkce
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: ff7e7b299d185b8db263d2076c1e075b87b487fc
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616395"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="b37e6-102">DestroyICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="b37e6-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="b37e6-103">Odstraní objekt [ICeeFileGen –](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="b37e6-103">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="b37e6-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b37e6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b37e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b37e6-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b37e6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b37e6-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="b37e6-107">pro `ICeeFileGen`Objekt, který se má zničit</span><span class="sxs-lookup"><span data-stu-id="b37e6-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b37e6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b37e6-108">Return Value</span></span>  
 <span data-ttu-id="b37e6-109">Tato metoda vrátí standardní kódy chyb modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b37e6-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b37e6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b37e6-110">Remarks</span></span>  
 <span data-ttu-id="b37e6-111">`DestroyICeeFileGen`odstraní `ICeeFileGen` objekt vytvořený funkcí [CreateICeeFileGen –](createiceefilegen-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b37e6-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b37e6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b37e6-112">Requirements</span></span>  
 <span data-ttu-id="b37e6-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b37e6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b37e6-114">**Hlavička:** ICeeFileGen –. h</span><span class="sxs-lookup"><span data-stu-id="b37e6-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="b37e6-115">**Knihovna:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="b37e6-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="b37e6-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b37e6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b37e6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b37e6-117">See also</span></span>

- [<span data-ttu-id="b37e6-118">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="b37e6-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
