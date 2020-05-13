---
title: 'ICorDebugMergedAssemblyRecord:: getssdp – metoda'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: f6c6682c8bb23143d308aa4f1a6887b28ea82fcd
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209705"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="c04da-102">ICorDebugMergedAssemblyRecord:: getssdp – metoda</span><span class="sxs-lookup"><span data-stu-id="c04da-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="c04da-103">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="c04da-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c04da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c04da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c04da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c04da-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c04da-106">pro Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c04da-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c04da-107">mimo Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c04da-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="c04da-108">Ukazatel na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="c04da-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c04da-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c04da-109">Remarks</span></span>  
 <span data-ttu-id="c04da-110">Tato metoda načte jednoduchý název sestavení (například System. Collections) bez přípony souboru, verze, jazykové verze nebo tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="c04da-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="c04da-111">Odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnosti ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="c04da-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c04da-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c04da-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c04da-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c04da-113">Requirements</span></span>  
 <span data-ttu-id="c04da-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c04da-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c04da-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c04da-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c04da-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c04da-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c04da-117">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c04da-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04da-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c04da-118">See also</span></span>

- [<span data-ttu-id="c04da-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c04da-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="c04da-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c04da-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
