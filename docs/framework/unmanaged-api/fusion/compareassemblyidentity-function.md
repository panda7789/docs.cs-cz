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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 652000367c19572f73296c704047830ce1c74574
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231035"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="840ab-102">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="840ab-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="840ab-103">Porovná dvě identit sestavení pro určení, zda jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="840ab-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="840ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="840ab-104">Syntax</span></span>  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="840ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="840ab-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="840ab-106">[in] Textovou identitu první sestavení v porovnání.</span><span class="sxs-lookup"><span data-stu-id="840ab-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="840ab-107">[in] Příznak logické hodnoty označující sjednocení zadané uživatelem pro `pwzAssemblyIdentity1`.</span><span class="sxs-lookup"><span data-stu-id="840ab-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="840ab-108">[in] Textovou identitu druhou sestavení v porovnání.</span><span class="sxs-lookup"><span data-stu-id="840ab-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="840ab-109">[in] Příznak logické hodnoty označující sjednocení zadané uživatelem pro `pwzAssemblyIdentity2`.</span><span class="sxs-lookup"><span data-stu-id="840ab-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="840ab-110">[out] Logický příznak, který určuje, zda daná dvě sestavení jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="840ab-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="840ab-111">[out] [Assemblycomparisonresult –](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) výčet, který obsahuje podrobné informace o porovnání.</span><span class="sxs-lookup"><span data-stu-id="840ab-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="840ab-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="840ab-112">Return Value</span></span>  
 <span data-ttu-id="840ab-113">`pfEquivalent` Vrátí logickou hodnotu, která určuje, zda daná dvě sestavení jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="840ab-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="840ab-114">`pResult` Vrátí jednu z `AssemblyComparisonResult` hodnot, které se poskytují podrobnější důvod pro hodnotu vlastnosti `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="840ab-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="840ab-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="840ab-115">Remarks</span></span>  
 <span data-ttu-id="840ab-116">`CompareAssemblyIdentity` kontroluje, zda `pwzAssemblyIdentity1` a `pwzAssemblyIdentity2` jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="840ab-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="840ab-117">`pfEquivalent` je nastavena na `true` v jedné nebo více z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="840ab-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="840ab-118">Identity dvě sestavení jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="840ab-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="840ab-119">Pro sestavení se silným názvem referenčních materiálech o ekvivalenci vyžaduje název sestavení, verzi, token veřejného klíče a jazykovou verzi být identické.</span><span class="sxs-lookup"><span data-stu-id="840ab-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="840ab-120">Pro sestavení s jednoduchým názvem referenčních materiálech o ekvivalenci vyžaduje shodu v názvu sestavení a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="840ab-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="840ab-121">Obě identit sestavení odkazovat na sestavení, které běží na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="840ab-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="840ab-122">Tato podmínka vrátí `true` i v případě, že číslo verze sestavení se neshodují.</span><span class="sxs-lookup"><span data-stu-id="840ab-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="840ab-123">Tato dvě sestavení nejsou spravovaná sestavení, ale `fUnified1` nebo `fUnified2` byl nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="840ab-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="840ab-124">`fUnified` Příznak určuje, že všechna čísla verzí až číslo verze sestavení se silným názvem jsou považovány za ekvivalentní k sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="840ab-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="840ab-125">Například pokud hodnota `pwzAssemblyIndentity1` je "MyAssembly, verze = 3.0.0.0, jazyková verze = neutral, publicKeyToken =..." a hodnota `fUnified1` je `true`, to znamená, že by měl být všechny verze MyAssembly z verze 0.0.0.0 k 3.0.0.0 považovány za ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="840ab-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="840ab-126">V takovém případě pokud `pwzAssemblyIndentity2` odkazuje na stejné sestavení jako `pwzAssemblyIndentity1`, s tím rozdílem, že má nižší číslo verze, `pfEquivalent` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="840ab-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="840ab-127">Pokud `pwzAssemblyIdentity2` odkazuje na vyšší číslo verze `pfEquivalent` je nastavena na `true` pouze tehdy, pokud hodnota `fUnified2` je `true`.</span><span class="sxs-lookup"><span data-stu-id="840ab-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="840ab-128">`pResult` Parametr obsahuje konkrétní informace o proč dvě sestavení jsou považovány za ekvivalentní, nebo není ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="840ab-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="840ab-129">Další informace najdete v tématu [assemblycomparisonresult – výčet](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="840ab-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="840ab-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="840ab-130">Requirements</span></span>  
 <span data-ttu-id="840ab-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="840ab-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="840ab-132">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="840ab-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="840ab-133">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="840ab-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="840ab-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="840ab-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="840ab-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="840ab-135">See also</span></span>

- [<span data-ttu-id="840ab-136">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="840ab-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="840ab-137">AssemblyComparisonResult – výčet</span><span class="sxs-lookup"><span data-stu-id="840ab-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
