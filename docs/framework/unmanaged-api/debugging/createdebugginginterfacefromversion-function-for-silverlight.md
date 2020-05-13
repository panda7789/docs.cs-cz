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
ms.openlocfilehash: f40345b09cae164660711b987f62130518736518
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208621"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="bf6cf-102">CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight</span><span class="sxs-lookup"><span data-stu-id="bf6cf-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>

<span data-ttu-id="bf6cf-103">Přijímá řetězec verze modulu CLR (Common Language Runtime), který je vrácen [funkcí CreateVersionStringFromModule –](createversionstringfrommodule-function.md)a vrací odpovídající rozhraní ladicího programu (obvykle [ICorDebug](icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="bf6cf-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf6cf-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf6cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf6cf-105">Parameters</span></span>  

 `szDebuggeeVersion`\
 <span data-ttu-id="bf6cf-106">pro Řetězec verze modulu CLR v cílovém laděného procesu, který je vrácen [funkcí CreateVersionStringFromModule –](createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="bf6cf-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`\
 <span data-ttu-id="bf6cf-107">mimo Ukazatel na ukazatel na objekt modelu COM ( `IUnknown` ).</span><span class="sxs-lookup"><span data-stu-id="bf6cf-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="bf6cf-108">Tento objekt bude převeden na objekt [ICorDebug](icordebug-interface.md) před jeho vrácením.</span><span class="sxs-lookup"><span data-stu-id="bf6cf-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf6cf-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bf6cf-109">Return Value</span></span>

 `S_OK`\
 <span data-ttu-id="bf6cf-110">`ppCordb`odkazuje na platný objekt, který implementuje rozhraní [rozhraní ICorDebug](icordebug-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bf6cf-110">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 `E_INVALIDARG`\
 <span data-ttu-id="bf6cf-111">Buď `szDebuggeeVersion` nebo `ppCordb` je null.</span><span class="sxs-lookup"><span data-stu-id="bf6cf-111">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 <span data-ttu-id="bf6cf-112">Nelze nalézt komponentu, která je nezbytná pro ladění CLR.</span><span class="sxs-lookup"><span data-stu-id="bf6cf-112">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="bf6cf-113">_Mscordbi. dll_ nebo _mscordaccore. dll_ se nepodařilo najít ve stejném adresáři jako cílový CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="bf6cf-113">Either _mscordbi.dll_ or _mscordaccore.dll_ was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 <span data-ttu-id="bf6cf-114">Mscordbi. dll nebo mscordaccore. dll není stejná jako verze cílového CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="bf6cf-114">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="bf6cf-115">`E_FAIL`(nebo jiné `E_` návratové kódy) </span><span class="sxs-lookup"><span data-stu-id="bf6cf-115">`E_FAIL` (or other `E_` return codes)</span></span>\
 <span data-ttu-id="bf6cf-116">Nelze vrátit [rozhraní ICorDebug](icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bf6cf-116">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf6cf-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf6cf-117">Remarks</span></span>

 <span data-ttu-id="bf6cf-118">Rozhraní, které je vráceno, poskytuje zařízení pro připojení k CLR v cílovém procesu a ladění spravovaného kódu, který je spuštěn modul CLR.</span><span class="sxs-lookup"><span data-stu-id="bf6cf-118">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf6cf-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf6cf-119">Requirements</span></span>

 <span data-ttu-id="bf6cf-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf6cf-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf6cf-121">**Záhlaví:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="bf6cf-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="bf6cf-122">**Knihovna:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="bf6cf-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="bf6cf-123">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="bf6cf-123">**.NET Framework Versions:** 3.5 SP1</span></span>
