---
title: ICorDebugProcess6::GetExportStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 118f52db63464b4c9355ba9ee7f330b996c5bf71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792246"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="dbc72-102">ICorDebugProcess6::GetExportStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="dbc72-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="dbc72-103">Poskytuje informace o exportovaných funkcích modulu runtime, které vám pomůžou krokovat se spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="dbc72-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbc72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbc72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbc72-105">Parameters</span></span>  
 <span data-ttu-id="dbc72-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="dbc72-106">pszExportName</span></span>  
 <span data-ttu-id="dbc72-107">pro Název běhové funkce exportu, jak je zapsán v exportní tabulce PE.</span><span class="sxs-lookup"><span data-stu-id="dbc72-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="dbc72-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="dbc72-108">invokeKind</span></span>  
 <span data-ttu-id="dbc72-109">mimo Ukazatel na člen výčtu [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) , který popisuje, jak vyexportovaná funkce bude vyvolávat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="dbc72-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="dbc72-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="dbc72-110">invokePurpose</span></span>  
 <span data-ttu-id="dbc72-111">mimo Ukazatel na člen výčtu [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) , který popisuje, proč exportovaná funkce bude volat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="dbc72-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbc72-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dbc72-112">Return Value</span></span>  
 <span data-ttu-id="dbc72-113">Metoda může vracet hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="dbc72-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="dbc72-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dbc72-114">Return value</span></span>|<span data-ttu-id="dbc72-115">Popis</span><span class="sxs-lookup"><span data-stu-id="dbc72-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="dbc72-116">Volání metody bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="dbc72-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="dbc72-117">`pInvokeKind` nebo `pInvokePurpose` je **null**.</span><span class="sxs-lookup"><span data-stu-id="dbc72-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="dbc72-118">Jiné neúspěšné `HRESULT` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dbc72-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="dbc72-119">Podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="dbc72-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbc72-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbc72-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dbc72-121">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dbc72-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc72-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbc72-122">Requirements</span></span>  
 <span data-ttu-id="dbc72-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbc72-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc72-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dbc72-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbc72-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dbc72-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbc72-126">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbc72-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc72-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbc72-127">See also</span></span>

- [<span data-ttu-id="dbc72-128">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbc72-128">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="dbc72-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dbc72-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
