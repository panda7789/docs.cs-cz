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
ms.openlocfilehash: 340d2de09562ea9b767203a7fa839cdc6b729b3b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860887"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="3f7b4-102">CreateCordbObject – funkce</span><span class="sxs-lookup"><span data-stu-id="3f7b4-102">CreateCordbObject Function</span></span>
<span data-ttu-id="3f7b4-103">Vytvoří rozhraní ladicího programu ([ICorDebug](icordebug-interface.md)), které poskytuje funkce pro vytvoření instance spravované relace ladění na vzdáleném procesu.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f7b4-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f7b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f7b4-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="3f7b4-106">pro Verze ladicího programu cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="3f7b4-107">Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="3f7b4-108">mimo Ukazatel na ukazatel na objekt, který bude převeden na rozhraní [ICorDebug](icordebug-interface.md) a vráceno.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f7b4-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3f7b4-109">Return Value</span></span>  
 <span data-ttu-id="3f7b4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f7b4-110">S_OK</span></span>  
 <span data-ttu-id="3f7b4-111">Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="3f7b4-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3f7b4-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="3f7b4-113">`ppCordb`má hodnotu null nebo `iDebuggerVersion` není CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="3f7b4-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3f7b4-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="3f7b4-115">Nelze přidělit dostatek paměti pro`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="3f7b4-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="3f7b4-116">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="3f7b4-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="3f7b4-117">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f7b4-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f7b4-118">Remarks</span></span>  
 <span data-ttu-id="3f7b4-119">Rozhraní [ICorDebug](icordebug-interface.md) , které je vráceno `ppCordb` v nástroji, je rozhraní ladění nejvyšší úrovně pro všechny spravované služby ladění.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7b4-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f7b4-120">Requirements</span></span>  
 <span data-ttu-id="3f7b4-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f7b4-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f7b4-122">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="3f7b4-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="3f7b4-123">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="3f7b4-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="3f7b4-124">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="3f7b4-124">**.NET Framework Versions:** 3.5 SP1</span></span>
