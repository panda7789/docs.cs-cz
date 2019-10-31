---
title: CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: 438af9f191f48a86207c3b343ba428eef2c1fabc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132206"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="a2279-102">CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight</span><span class="sxs-lookup"><span data-stu-id="a2279-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="a2279-103">Přijímá řetězec verze modulu CLR (Common Language Runtime), který je vrácen [funkcí CreateVersionStringFromModule –](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)a vrací odpovídající rozhraní ladicího programu (obvykle [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="a2279-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2279-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2279-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2279-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2279-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="a2279-106">pro Řetězec verze modulu CLR v cílovém laděného procesu, který je vrácen [funkcí CreateVersionStringFromModule –](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="a2279-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="a2279-107">mimo Ukazatel na ukazatel na objekt modelu COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="a2279-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="a2279-108">Tento objekt bude převeden na objekt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) před jeho vrácením.</span><span class="sxs-lookup"><span data-stu-id="a2279-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2279-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a2279-109">Return Value</span></span>  
 <span data-ttu-id="a2279-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2279-110">S_OK</span></span>  
 <span data-ttu-id="a2279-111">`ppCordb` odkazuje na platný objekt, který implementuje rozhraní [rozhraní ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a2279-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="a2279-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a2279-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="a2279-113">Buď `szDebuggeeVersion`, nebo `ppCordb` je null.</span><span class="sxs-lookup"><span data-stu-id="a2279-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="a2279-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="a2279-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="a2279-115">Nelze nalézt komponentu, která je nezbytná pro ladění CLR.</span><span class="sxs-lookup"><span data-stu-id="a2279-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="a2279-116">To znamená, že soubor mscordbi. dll nebo mscordaccore. dll nebyl nalezen ve stejném adresáři jako cílový CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="a2279-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a2279-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="a2279-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="a2279-118">Mscordbi. dll nebo mscordaccore. dll není stejná jako verze cílového CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="a2279-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a2279-119">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="a2279-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a2279-120">Nelze vrátit [rozhraní ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a2279-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2279-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2279-121">Remarks</span></span>  
 <span data-ttu-id="a2279-122">Rozhraní, které je vráceno, poskytuje zařízení pro připojení k CLR v cílovém procesu a ladění spravovaného kódu, který je spuštěn modul CLR.</span><span class="sxs-lookup"><span data-stu-id="a2279-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2279-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2279-123">Requirements</span></span>  
 <span data-ttu-id="a2279-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2279-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2279-125">**Záhlaví:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="a2279-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a2279-126">**Knihovna:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="a2279-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a2279-127">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a2279-127">**.NET Framework Versions:** 3.5 SP1</span></span>
