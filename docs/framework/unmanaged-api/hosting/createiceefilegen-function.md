---
title: CreateICeeFileGen – funkce
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 294b82efd66704014aab1b73171afe9165f17664
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616447"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="26b01-102">CreateICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="26b01-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="26b01-103">Vytvoří objekt [ICeeFileGen –](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="26b01-103">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="26b01-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="26b01-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b01-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26b01-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26b01-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="26b01-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="26b01-107">mimo Ukazatel na adresu nového `ICeeFileGen` objektu.</span><span class="sxs-lookup"><span data-stu-id="26b01-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26b01-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26b01-108">Return Value</span></span>  
 <span data-ttu-id="26b01-109">Tato metoda vrátí standardní kódy chyb modelu COM.</span><span class="sxs-lookup"><span data-stu-id="26b01-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26b01-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26b01-110">Remarks</span></span>  
 <span data-ttu-id="26b01-111">`ICeeFileGen`Objekt se používá k vytvoření přenosných spustitelných souborů (PE) pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="26b01-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="26b01-112">Po dokončení volejte funkci [DestroyICeeFileGen –](destroyiceefilegen-function.md) pro zničení `ICeeFileGen` objektu.</span><span class="sxs-lookup"><span data-stu-id="26b01-112">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b01-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26b01-113">Requirements</span></span>  
 <span data-ttu-id="26b01-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26b01-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b01-115">**Hlavička:** ICeeFileGen –. h</span><span class="sxs-lookup"><span data-stu-id="26b01-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="26b01-116">**Knihovna:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="26b01-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="26b01-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b01-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b01-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="26b01-118">See also</span></span>

- [<span data-ttu-id="26b01-119">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="26b01-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
