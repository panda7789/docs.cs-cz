---
title: ICorDebugAppDomain::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7939f7b1c0c725bb4e8c642bc38121dd755da5e2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471049"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="65d8b-102">ICorDebugAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="65d8b-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="65d8b-103">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d8b-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65d8b-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65d8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65d8b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="65d8b-106">[in] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="65d8b-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="65d8b-107">Tuto hodnotu nastavte na hodnotu nula, tato metoda uvést do režimu dotazu.</span><span class="sxs-lookup"><span data-stu-id="65d8b-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="65d8b-108">[out] Ukazatel na velikost název nebo počet znaků ve skutečnosti vrátí v `szName`.</span><span class="sxs-lookup"><span data-stu-id="65d8b-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="65d8b-109">V režimu dotazu, tato hodnota umožňuje volajícímu vědět, jak velkou vyrovnávací paměti k přidělení pro název.</span><span class="sxs-lookup"><span data-stu-id="65d8b-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="65d8b-110">[out] Pole uchovávající název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d8b-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65d8b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65d8b-111">Remarks</span></span>  
 <span data-ttu-id="65d8b-112">Ladicí program volá `GetName` jednou metodu k získání velikost vyrovnávací paměti, třeba název.</span><span class="sxs-lookup"><span data-stu-id="65d8b-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="65d8b-113">Ladicí program přiděluje vyrovnávací paměti a potom volá metodu podruhé tak, aby vyplnil vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="65d8b-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="65d8b-114">První volání, získat její velikost názvu, se označuje jako *režim dotazů*.</span><span class="sxs-lookup"><span data-stu-id="65d8b-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d8b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65d8b-115">Requirements</span></span>  
 <span data-ttu-id="65d8b-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65d8b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d8b-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65d8b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65d8b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65d8b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65d8b-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d8b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
