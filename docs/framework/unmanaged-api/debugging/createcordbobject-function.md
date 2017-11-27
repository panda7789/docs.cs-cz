---
title: "CreateCordbObject – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateCoredbObject
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06e08148e5526d65d82eca52ffe8db66a4e7df6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="createcordbobject-function"></a><span data-ttu-id="7be4a-102">CreateCordbObject – funkce</span><span class="sxs-lookup"><span data-stu-id="7be4a-102">CreateCordbObject Function</span></span>
<span data-ttu-id="7be4a-103">Vytvoří rozhraní ladicího programu ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)), poskytuje funkce pro vytváření instancí spravované ladicí relace na vzdálený proces.</span><span class="sxs-lookup"><span data-stu-id="7be4a-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7be4a-104">Syntax</span></span>  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7be4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7be4a-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="7be4a-106">[v] Ladicí program verze tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="7be4a-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="7be4a-107">Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="7be4a-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="7be4a-108">[out] Ukazatel na ukazatel na objekt, který bude přetypovat [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní a vrácena.</span><span class="sxs-lookup"><span data-stu-id="7be4a-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7be4a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7be4a-109">Return Value</span></span>  
 <span data-ttu-id="7be4a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7be4a-110">S_OK</span></span>  
 <span data-ttu-id="7be4a-111">Počet CLRs v procesu byla úspěšně zjistit a byly správně zadat odpovídající popisovač a cesta pole.</span><span class="sxs-lookup"><span data-stu-id="7be4a-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="7be4a-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7be4a-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="7be4a-113">`ppCordb`má hodnotu null, nebo `iDebuggerVersion` není CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="7be4a-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="7be4a-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7be4a-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="7be4a-115">Nelze přidělit dostatek paměti pro`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="7be4a-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="7be4a-116">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="7be4a-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7be4a-117">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="7be4a-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7be4a-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7be4a-118">Remarks</span></span>  
 <span data-ttu-id="7be4a-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní, které je vrácený v `ppCordb` je nejvyšší úrovně ladění rozhraní pro všechny spravované ladění služeb.</span><span class="sxs-lookup"><span data-stu-id="7be4a-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be4a-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7be4a-120">Requirements</span></span>  
 <span data-ttu-id="7be4a-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7be4a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7be4a-122">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="7be4a-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7be4a-123">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="7be4a-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7be4a-124">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7be4a-124">**.NET Framework Versions:** 3.5 SP1</span></span>
