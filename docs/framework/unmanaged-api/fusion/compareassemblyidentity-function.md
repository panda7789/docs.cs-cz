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
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795443"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="4283e-102">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="4283e-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="4283e-103">Porovná dvě identity sestavení a určí, zda jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4283e-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4283e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4283e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4283e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4283e-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="4283e-106">pro Textová identita prvního sestavení v porovnání</span><span class="sxs-lookup"><span data-stu-id="4283e-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="4283e-107">pro Logický příznak, který označuje, že uživatel zadal sjednocení `pwzAssemblyIdentity1`pro.</span><span class="sxs-lookup"><span data-stu-id="4283e-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="4283e-108">pro Textová identita druhého sestavení v porovnání</span><span class="sxs-lookup"><span data-stu-id="4283e-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="4283e-109">pro Logický příznak, který označuje, že uživatel zadal sjednocení `pwzAssemblyIdentity2`pro.</span><span class="sxs-lookup"><span data-stu-id="4283e-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="4283e-110">mimo Logický příznak, který označuje, zda jsou dvě sestavení ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4283e-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="4283e-111">mimo Výčet [AssemblyComparisonResult –](assemblycomparisonresult-enumeration.md) , který obsahuje podrobné informace o porovnání.</span><span class="sxs-lookup"><span data-stu-id="4283e-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4283e-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4283e-112">Return Value</span></span>  
 <span data-ttu-id="4283e-113">`pfEquivalent`vrací logickou hodnotu, která označuje, zda jsou dvě sestavení ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4283e-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="4283e-114">`pResult`Vrátí jednu z `AssemblyComparisonResult` hodnot, která poskytne podrobnější důvod pro `pfEquivalent`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4283e-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4283e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4283e-115">Remarks</span></span>  
 <span data-ttu-id="4283e-116">`CompareAssemblyIdentity`kontroluje, `pwzAssemblyIdentity1` zda `pwzAssemblyIdentity2` a jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4283e-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="4283e-117">`pfEquivalent`je nastaveno na `true` jednu nebo více z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="4283e-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="4283e-118">Dvě identity sestavení jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4283e-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="4283e-119">Pro silně pojmenovaná sestavení ekvivalence vyžaduje, aby byl název sestavení, verze, token veřejného klíče a jazyková verze identické.</span><span class="sxs-lookup"><span data-stu-id="4283e-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="4283e-120">U jednoduše pojmenovaných sestavení vyžaduje ekvivalenci shodu s názvem sestavení a kulturou.</span><span class="sxs-lookup"><span data-stu-id="4283e-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="4283e-121">Obě identity sestavení odkazují na sestavení, která běží na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4283e-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="4283e-122">Tento stav vrátí `true` i v případě, že čísla verzí sestavení se neshodují.</span><span class="sxs-lookup"><span data-stu-id="4283e-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="4283e-123">Tato dvě sestavení nejsou spravovaná sestavení, ale `fUnified1` nebo `fUnified2` byla nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="4283e-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="4283e-124">`fUnified` Příznak označuje, že všechna čísla verzí až do čísla verze sestavení se silným názvem se považují za ekvivalent sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="4283e-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="4283e-125">Pokud je například hodnota `pwzAssemblyIndentity1` "MyAssembly, Version = 3.0.0.0, Culture = neutral, PublicKeyToken =...." a `fUnified1` hodnota je `true`, znamená to, že by měly být všechny verze MyAssembly od verze 0.0.0.0 až 3.0.0.0. považován za ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4283e-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="4283e-126">Pokud `pwzAssemblyIndentity2` v takovém případě odkazuje na stejné sestavení jako `pwzAssemblyIndentity1`s tím rozdílem, že má nižší číslo verze, `pfEquivalent` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="4283e-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="4283e-127">Pokud `pwzAssemblyIdentity2` odkazuje na vyšší číslo verze, je `pfEquivalent` nastavena na `true` hodnotu pouze v případě, že `fUnified2` je `true`hodnota.</span><span class="sxs-lookup"><span data-stu-id="4283e-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="4283e-128">`pResult` Parametr zahrnuje konkrétní informace o tom, proč jsou tato dvě sestavení považována za ekvivalentní nebo neekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4283e-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="4283e-129">Další informace najdete v tématu [výčet AssemblyComparisonResult –](assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4283e-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4283e-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4283e-130">Requirements</span></span>  
 <span data-ttu-id="4283e-131">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4283e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4283e-132">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4283e-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4283e-133">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4283e-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4283e-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4283e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4283e-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4283e-135">See also</span></span>

- [<span data-ttu-id="4283e-136">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="4283e-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="4283e-137">AssemblyComparisonResult – výčet</span><span class="sxs-lookup"><span data-stu-id="4283e-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
