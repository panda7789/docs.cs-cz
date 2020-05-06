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
ms.openlocfilehash: c83bdcca4fab75b4ae94500ceb785b6000cd802a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860864"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="fb370-102">CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight</span><span class="sxs-lookup"><span data-stu-id="fb370-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="fb370-103">Přijímá řetězec verze modulu CLR (Common Language Runtime), který je vrácen [funkcí CreateVersionStringFromModule –](createversionstringfrommodule-function.md)a vrací odpovídající rozhraní ladicího programu (obvykle [ICorDebug](icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="fb370-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb370-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb370-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb370-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb370-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="fb370-106">pro Řetězec verze modulu CLR v cílovém laděného procesu, který je vrácen [funkcí CreateVersionStringFromModule –](createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="fb370-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="fb370-107">mimo Ukazatel na ukazatel na objekt modelu COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="fb370-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="fb370-108">Tento objekt bude převeden na objekt [ICorDebug](icordebug-interface.md) před jeho vrácením.</span><span class="sxs-lookup"><span data-stu-id="fb370-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb370-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb370-109">Return Value</span></span>  
 <span data-ttu-id="fb370-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb370-110">S_OK</span></span>  
 <span data-ttu-id="fb370-111">`ppCordb`odkazuje na platný objekt, který implementuje rozhraní [rozhraní ICorDebug](icordebug-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fb370-111">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="fb370-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fb370-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="fb370-113">Buď `szDebuggeeVersion` nebo `ppCordb` je null.</span><span class="sxs-lookup"><span data-stu-id="fb370-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="fb370-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="fb370-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="fb370-115">Nelze nalézt komponentu, která je nezbytná pro ladění CLR.</span><span class="sxs-lookup"><span data-stu-id="fb370-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="fb370-116">To znamená, že soubor mscordbi. dll nebo mscordaccore. dll nebyl nalezen ve stejném adresáři jako cílový CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="fb370-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="fb370-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="fb370-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="fb370-118">Mscordbi. dll nebo mscordaccore. dll není stejná jako verze cílového CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="fb370-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="fb370-119">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="fb370-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fb370-120">Nelze vrátit [rozhraní ICorDebug](icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="fb370-120">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb370-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb370-121">Remarks</span></span>  
 <span data-ttu-id="fb370-122">Rozhraní, které je vráceno, poskytuje zařízení pro připojení k CLR v cílovém procesu a ladění spravovaného kódu, který je spuštěn modul CLR.</span><span class="sxs-lookup"><span data-stu-id="fb370-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb370-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb370-123">Requirements</span></span>  
 <span data-ttu-id="fb370-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb370-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb370-125">**Záhlaví:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="fb370-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="fb370-126">**Knihovna:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="fb370-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="fb370-127">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="fb370-127">**.NET Framework Versions:** 3.5 SP1</span></span>
