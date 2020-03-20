---
title: ICorDebugMergedAssemblyRecord::Metoda GetSimpleName
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 99ba27171e129e8725c3e0555a6991ef08b893da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178709"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="bcc3b-102">ICorDebugMergedAssemblyRecord::Metoda GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="bcc3b-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="bcc3b-103">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="bcc3b-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcc3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcc3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcc3b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="bcc3b-106">[v] Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bcc3b-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bcc3b-107">[out] Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bcc3b-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="bcc3b-108">Ukazatel na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="bcc3b-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcc3b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcc3b-109">Remarks</span></span>  
 <span data-ttu-id="bcc3b-110">Tato metoda načte jednoduchý název sestavení (například "System.Collections"), bez přípony souboru, verze, jazykové verze nebo tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="bcc3b-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="bcc3b-111">Odpovídá vlastnosti <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="bcc3b-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcc3b-112">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="bcc3b-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcc3b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcc3b-113">Requirements</span></span>  
 <span data-ttu-id="bcc3b-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcc3b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcc3b-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcc3b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcc3b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcc3b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcc3b-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcc3b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc3b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcc3b-118">See also</span></span>

- [<span data-ttu-id="bcc3b-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcc3b-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="bcc3b-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcc3b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
