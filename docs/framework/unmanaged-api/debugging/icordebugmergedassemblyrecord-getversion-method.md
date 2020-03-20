---
title: ICorDebugMergedAssemblyRecord::Metoda GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 5dc9995e88086da854d2e9382cef81b229ff9dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178688"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="6acfa-102">ICorDebugMergedAssemblyRecord::Metoda GetVersion</span><span class="sxs-lookup"><span data-stu-id="6acfa-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="6acfa-103">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="6acfa-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6acfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6acfa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6acfa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6acfa-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="6acfa-106">[out] Ukazatel na číslo hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="6acfa-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="6acfa-107">[out] Ukazatel na číslo dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="6acfa-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="6acfa-108">[out] Ukazatel na číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="6acfa-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="6acfa-109">[out] Ukazatel na číslo revize.</span><span class="sxs-lookup"><span data-stu-id="6acfa-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6acfa-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6acfa-110">Remarks</span></span>  
 <span data-ttu-id="6acfa-111">Informace o číslech verzí <xref:System.Version> sestavení naleznete v tématu třídy.</span><span class="sxs-lookup"><span data-stu-id="6acfa-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6acfa-112">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="6acfa-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6acfa-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6acfa-113">Requirements</span></span>  
 <span data-ttu-id="6acfa-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6acfa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6acfa-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6acfa-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6acfa-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6acfa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6acfa-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6acfa-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6acfa-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6acfa-118">See also</span></span>

- [<span data-ttu-id="6acfa-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6acfa-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="6acfa-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6acfa-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
