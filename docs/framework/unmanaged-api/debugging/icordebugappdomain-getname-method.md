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
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179093"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="a7ae0-102">ICorDebugAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="a7ae0-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="a7ae0-103">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7ae0-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ae0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7ae0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7ae0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7ae0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a7ae0-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="a7ae0-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="a7ae0-107">Nastavte tuto hodnotu na nulu, aby tuto metodu v režimu dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7ae0-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a7ae0-108">[out] Ukazatel na velikost názvu nebo počet znaků skutečně `szName`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="a7ae0-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="a7ae0-109">V režimu dotazu tato hodnota umožňuje volajícímu vědět, jak velké vyrovnávací paměti přidělit pro název.</span><span class="sxs-lookup"><span data-stu-id="a7ae0-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="a7ae0-110">[out] Pole, které ukládá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7ae0-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ae0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7ae0-111">Remarks</span></span>  
 <span data-ttu-id="a7ae0-112">Ladicí program `GetName` volá metodu jednou získat velikost vyrovnávací paměti potřebné pro název.</span><span class="sxs-lookup"><span data-stu-id="a7ae0-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="a7ae0-113">Ladicí program přidělí vyrovnávací paměť a potom volá metodu podruhé k vyplnění vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a7ae0-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="a7ae0-114">První volání, chcete-li získat velikost názvu, se označuje jako *režim dotazu*.</span><span class="sxs-lookup"><span data-stu-id="a7ae0-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ae0-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7ae0-115">Requirements</span></span>  
 <span data-ttu-id="a7ae0-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ae0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ae0-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7ae0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7ae0-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7ae0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7ae0-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ae0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
