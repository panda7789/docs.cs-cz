---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: 015735e1c6c3b6c146f2fca3a9bdc28baeca2f92
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792512"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="13f21-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="13f21-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="13f21-103">Získá aktuální nastavení příznaku kompilátoru, které modul CLR (Common Language Runtime) používá k výběru správného předkompilovaného (nativně) image, která se má načíst do tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="13f21-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13f21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13f21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13f21-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="13f21-106">mimo Ukazatel na bitovou kombinaci hodnot výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) , které se používají k výběru správné předkompilované image, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="13f21-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13f21-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13f21-107">Remarks</span></span>  
 <span data-ttu-id="13f21-108">Použijte metodu [ICorDebugProcess2:: SetDesiredNGENCompilerFlags –](icordebugprocess2-setdesiredngencompilerflags-method.md) k nastavení příznaků, které bude modul CLR používat k výběru správné předkompilované bitové kopie, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="13f21-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13f21-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13f21-109">Requirements</span></span>  
 <span data-ttu-id="13f21-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13f21-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f21-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="13f21-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13f21-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="13f21-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13f21-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f21-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
