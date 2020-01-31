---
title: CreateCordbObject – funkce
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 1d190c5b558c7c523be09267e59eab7c5611563a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793861"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="0304f-102">CreateCordbObject – funkce</span><span class="sxs-lookup"><span data-stu-id="0304f-102">CreateCordbObject Function</span></span>
<span data-ttu-id="0304f-103">Vytvoří rozhraní ladicího programu ([ICorDebug](icordebug-interface.md)), které poskytuje funkce pro vytvoření instance spravované relace ladění na vzdáleném procesu.</span><span class="sxs-lookup"><span data-stu-id="0304f-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0304f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0304f-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0304f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0304f-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="0304f-106">pro Verze ladicího programu cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="0304f-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="0304f-107">Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="0304f-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="0304f-108">mimo Ukazatel na ukazatel na objekt, který bude převeden na rozhraní [ICorDebug](icordebug-interface.md) a vráceno.</span><span class="sxs-lookup"><span data-stu-id="0304f-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0304f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0304f-109">Return Value</span></span>  
 <span data-ttu-id="0304f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0304f-110">S_OK</span></span>  
 <span data-ttu-id="0304f-111">Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.</span><span class="sxs-lookup"><span data-stu-id="0304f-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="0304f-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0304f-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="0304f-113">`ppCordb` je null nebo `iDebuggerVersion` není CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="0304f-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="0304f-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0304f-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="0304f-115">Nelze přidělit dostatek paměti pro `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="0304f-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="0304f-116">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="0304f-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="0304f-117">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="0304f-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0304f-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0304f-118">Remarks</span></span>  
 <span data-ttu-id="0304f-119">Rozhraní [ICorDebug](icordebug-interface.md) , které je vráceno v `ppCordb`, je rozhraní ladění nejvyšší úrovně pro všechny spravované služby ladění.</span><span class="sxs-lookup"><span data-stu-id="0304f-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0304f-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0304f-120">Requirements</span></span>  
 <span data-ttu-id="0304f-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0304f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0304f-122">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="0304f-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0304f-123">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="0304f-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0304f-124">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="0304f-124">**.NET Framework Versions:** 3.5 SP1</span></span>
