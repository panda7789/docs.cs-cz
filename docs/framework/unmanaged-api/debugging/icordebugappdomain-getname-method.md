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
ms.openlocfilehash: 2c9aa6792885c685195049948a540453b1f5235e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110313"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="9be41-102">ICorDebugAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="9be41-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="9be41-103">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9be41-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9be41-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9be41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9be41-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9be41-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="9be41-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="9be41-107">Nastavte tuto hodnotu na nula pro vložení této metody do režimu dotazu.</span><span class="sxs-lookup"><span data-stu-id="9be41-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9be41-108">mimo Ukazatel na velikost názvu nebo počet znaků, které jsou ve skutečnosti vráceny v `szName`.</span><span class="sxs-lookup"><span data-stu-id="9be41-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="9be41-109">V režimu dotazu tato hodnota umožňuje volajícímu zjistit, jak velký má vyrovnávací paměť přidělit pro název.</span><span class="sxs-lookup"><span data-stu-id="9be41-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="9be41-110">mimo Pole, ve kterém je uložen název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9be41-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9be41-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9be41-111">Remarks</span></span>  
 <span data-ttu-id="9be41-112">Ladicí program volá metodu `GetName` jednou, aby získala velikost vyrovnávací paměti potřebné pro název.</span><span class="sxs-lookup"><span data-stu-id="9be41-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="9be41-113">Ladicí program přidělí vyrovnávací paměť a poté zavolá metodu za sekundu, aby vyplnila vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="9be41-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="9be41-114">První volání, pro získání velikosti názvu, je označováno jako *režim dotazu*.</span><span class="sxs-lookup"><span data-stu-id="9be41-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9be41-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9be41-115">Requirements</span></span>  
 <span data-ttu-id="9be41-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9be41-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9be41-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9be41-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9be41-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9be41-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9be41-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9be41-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
