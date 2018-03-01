---
title: "CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c38171c5887bb207b3692e9fa92aa2be2bc72a27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="4c338-102">CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight</span><span class="sxs-lookup"><span data-stu-id="4c338-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="4c338-103">Přijímá běžné language runtime (CLR) verze řetězec, který je vrácena z [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)a vrátí odpovídající rozhraní ladicího programu (obvykle [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="4c338-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c338-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c338-104">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c338-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c338-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="4c338-106">[v] Řetězec verze modulu CLR cíl ladění, která je vrácena [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="4c338-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="4c338-107">[out] Ukazatel na ukazatel na objekt COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="4c338-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="4c338-108">Tento objekt přetypovat [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objektu před vrácením.</span><span class="sxs-lookup"><span data-stu-id="4c338-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c338-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4c338-109">Return Value</span></span>  
 <span data-ttu-id="4c338-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c338-110">S_OK</span></span>  
 <span data-ttu-id="4c338-111">`ppCordb`odkazuje na platný objekt, který implementuje [ICorDebug rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4c338-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="4c338-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4c338-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="4c338-113">Buď `szDebuggeeVersion` nebo `ppCordb` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4c338-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="4c338-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="4c338-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="4c338-115">Součásti, které jsou nezbytné pro ladění CLR nelze najít.</span><span class="sxs-lookup"><span data-stu-id="4c338-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="4c338-116">To znamená, že mscordbi.dll nebo mscordaccore.dll nebyl nalezen ve stejném adresáři jako cíl CoreCLR.dll.</span><span class="sxs-lookup"><span data-stu-id="4c338-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="4c338-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="4c338-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="4c338-118">Mscordbi.dll nebo mscordaccore.dll není stejnou verzi jako cíl CoreCLR.dll.</span><span class="sxs-lookup"><span data-stu-id="4c338-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="4c338-119">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="4c338-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4c338-120">Nelze vrátit [ICorDebug rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4c338-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c338-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c338-121">Remarks</span></span>  
 <span data-ttu-id="4c338-122">Rozhraní, která je vrácena zajišťuje funkce pro připojení k CLR v Cílový proces a ladění spravovaného kódu, který je spuštěn modul CLR.</span><span class="sxs-lookup"><span data-stu-id="4c338-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c338-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c338-123">Requirements</span></span>  
 <span data-ttu-id="4c338-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c338-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c338-125">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="4c338-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="4c338-126">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="4c338-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="4c338-127">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="4c338-127">**.NET Framework Versions:** 3.5 SP1</span></span>
