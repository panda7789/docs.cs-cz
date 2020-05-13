---
title: 'ICorDebugMergedAssemblyRecord:: GetVersion – metoda'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: cad71080c86e92beb318722db86011b09ce02e91
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207628"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="6be4c-102">ICorDebugMergedAssemblyRecord:: GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="6be4c-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="6be4c-103">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="6be4c-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6be4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6be4c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6be4c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6be4c-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="6be4c-106">mimo Ukazatel na hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="6be4c-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="6be4c-107">mimo Ukazatel na číslo dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="6be4c-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="6be4c-108">mimo Ukazatel na číslo buildu.</span><span class="sxs-lookup"><span data-stu-id="6be4c-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="6be4c-109">mimo Ukazatel na číslo revize.</span><span class="sxs-lookup"><span data-stu-id="6be4c-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6be4c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6be4c-110">Remarks</span></span>  
 <span data-ttu-id="6be4c-111">Informace o číslech verzí sestavení naleznete v <xref:System.Version> tématu třídy.</span><span class="sxs-lookup"><span data-stu-id="6be4c-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6be4c-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6be4c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6be4c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6be4c-113">Requirements</span></span>  
 <span data-ttu-id="6be4c-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6be4c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6be4c-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6be4c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6be4c-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6be4c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6be4c-117">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6be4c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be4c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6be4c-118">See also</span></span>

- [<span data-ttu-id="6be4c-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be4c-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="6be4c-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be4c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
