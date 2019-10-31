---
title: CompareAssemblyIdentity – funkce
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
ms.openlocfilehash: f6711902fb9d5c5c16084057b731746843cf0230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108912"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="51b44-102">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="51b44-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="51b44-103">Porovná dvě identity sestavení a určí, zda jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="51b44-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51b44-104">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="51b44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51b44-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="51b44-106">pro Textová identita prvního sestavení v porovnání</span><span class="sxs-lookup"><span data-stu-id="51b44-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="51b44-107">pro Logický příznak, který označuje, že uživatel zadal sjednocení pro `pwzAssemblyIdentity1`.</span><span class="sxs-lookup"><span data-stu-id="51b44-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="51b44-108">pro Textová identita druhého sestavení v porovnání</span><span class="sxs-lookup"><span data-stu-id="51b44-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="51b44-109">pro Logický příznak, který označuje, že uživatel zadal sjednocení pro `pwzAssemblyIdentity2`.</span><span class="sxs-lookup"><span data-stu-id="51b44-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="51b44-110">mimo Logický příznak, který označuje, zda jsou dvě sestavení ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="51b44-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="51b44-111">mimo Výčet [AssemblyComparisonResult –](assemblycomparisonresult-enumeration.md) , který obsahuje podrobné informace o porovnání.</span><span class="sxs-lookup"><span data-stu-id="51b44-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51b44-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51b44-112">Return Value</span></span>  
 <span data-ttu-id="51b44-113">`pfEquivalent` vrací logickou hodnotu, která označuje, zda jsou dvě sestavení ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="51b44-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="51b44-114">`pResult` vrátí jednu z hodnot `AssemblyComparisonResult` a poskytne podrobnější důvod pro hodnotu `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="51b44-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51b44-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51b44-115">Remarks</span></span>  
 <span data-ttu-id="51b44-116">`CompareAssemblyIdentity` kontroluje, zda jsou `pwzAssemblyIdentity1` a `pwzAssemblyIdentity2` ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="51b44-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="51b44-117">`pfEquivalent` je nastavené na `true` v jedné nebo několika následujících podmínkách:</span><span class="sxs-lookup"><span data-stu-id="51b44-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="51b44-118">Dvě identity sestavení jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="51b44-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="51b44-119">Pro silně pojmenovaná sestavení ekvivalence vyžaduje, aby byl název sestavení, verze, token veřejného klíče a jazyková verze identické.</span><span class="sxs-lookup"><span data-stu-id="51b44-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="51b44-120">U jednoduše pojmenovaných sestavení vyžaduje ekvivalenci shodu s názvem sestavení a kulturou.</span><span class="sxs-lookup"><span data-stu-id="51b44-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="51b44-121">Obě identity sestavení odkazují na sestavení, která běží na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51b44-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="51b44-122">Tento stav vrátí `true` i v případě, že čísla verzí sestavení se neshodují.</span><span class="sxs-lookup"><span data-stu-id="51b44-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="51b44-123">Tato dvě sestavení nejsou spravovaná sestavení, ale `fUnified1` nebo `fUnified2` byla nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="51b44-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="51b44-124">Příznak `fUnified` označuje, že všechna čísla verzí až do čísla verze sestavení se silným názvem se považují za ekvivalentní silně pojmenovanému sestavení.</span><span class="sxs-lookup"><span data-stu-id="51b44-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="51b44-125">Pokud je například hodnota `pwzAssemblyIndentity1` "MyAssembly, Version = 3.0.0.0, Culture = neutral, publicKeyToken =...." a hodnota `fUnified1` je `true`, znamená to, že všechny verze MyAssembly z verze 0.0.0.0 na 3.0.0.0 by měly být považovány za stejného.</span><span class="sxs-lookup"><span data-stu-id="51b44-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="51b44-126">V takovém případě, pokud `pwzAssemblyIndentity2` odkazuje na stejné sestavení jako `pwzAssemblyIndentity1`, s tím rozdílem, že má nižší číslo verze, `pfEquivalent` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="51b44-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="51b44-127">Pokud `pwzAssemblyIdentity2` odkazuje na vyšší číslo verze, `pfEquivalent` je nastaveno na `true` pouze v případě, že je `true`hodnota `fUnified2`.</span><span class="sxs-lookup"><span data-stu-id="51b44-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="51b44-128">Parametr `pResult` obsahuje konkrétní informace o tom, proč jsou tato dvě sestavení považována za ekvivalentní nebo neekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="51b44-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="51b44-129">Další informace najdete v tématu [výčet AssemblyComparisonResult –](assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="51b44-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b44-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51b44-130">Requirements</span></span>  
 <span data-ttu-id="51b44-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b44-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b44-132">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="51b44-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="51b44-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51b44-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51b44-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b44-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b44-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51b44-135">See also</span></span>

- [<span data-ttu-id="51b44-136">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="51b44-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="51b44-137">AssemblyComparisonResult – výčet</span><span class="sxs-lookup"><span data-stu-id="51b44-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
