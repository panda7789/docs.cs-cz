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
ms.openlocfilehash: 3db37576f5da7b26e7bd9d3343f8bb8b97f2ba82
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895232"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="852e1-102">ICorDebugAppDomain::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="852e1-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="852e1-103">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="852e1-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="852e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="852e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="852e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="852e1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="852e1-106">pro Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="852e1-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="852e1-107">Nastavte tuto hodnotu na nula pro vložení této metody do režimu dotazu.</span><span class="sxs-lookup"><span data-stu-id="852e1-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="852e1-108">mimo Ukazatel na velikost názvu nebo počet skutečně vrácených znaků `szName`.</span><span class="sxs-lookup"><span data-stu-id="852e1-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="852e1-109">V režimu dotazu tato hodnota umožňuje volajícímu zjistit, jak velký má vyrovnávací paměť přidělit pro název.</span><span class="sxs-lookup"><span data-stu-id="852e1-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="852e1-110">mimo Pole, ve kterém je uložen název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="852e1-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="852e1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="852e1-111">Remarks</span></span>  
 <span data-ttu-id="852e1-112">Ladicí program volá `GetName` metodu jednou, aby získala velikost vyrovnávací paměti potřebné pro název.</span><span class="sxs-lookup"><span data-stu-id="852e1-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="852e1-113">Ladicí program přidělí vyrovnávací paměť a poté zavolá metodu za sekundu, aby vyplnila vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="852e1-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="852e1-114">První volání, pro získání velikosti názvu, je označováno jako *režim dotazu*.</span><span class="sxs-lookup"><span data-stu-id="852e1-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="852e1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="852e1-115">Requirements</span></span>  
 <span data-ttu-id="852e1-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="852e1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="852e1-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="852e1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="852e1-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="852e1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="852e1-119">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="852e1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
