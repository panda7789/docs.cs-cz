---
title: ICorDebugModule::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7f62385031967c164915fd31735a6d962f557fa
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894984"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="94b86-102">ICorDebugModule::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="94b86-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="94b86-103">Získá název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="94b86-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94b86-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94b86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94b86-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="94b86-106">pro Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="94b86-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="94b86-107">pro Ukazatel na délku vráceného názvu.</span><span class="sxs-lookup"><span data-stu-id="94b86-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="94b86-108">mimo Pole, ve kterém je uložený vrácený název.</span><span class="sxs-lookup"><span data-stu-id="94b86-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94b86-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94b86-109">Remarks</span></span>  
 <span data-ttu-id="94b86-110">`GetName` Metoda vrátí hodnotu S_OK HRESULT, pokud se název souboru modulu shoduje s názvem na disku.</span><span class="sxs-lookup"><span data-stu-id="94b86-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="94b86-111">`GetName`Vrátí S_FALSE HRESULT, pokud je název založen, například pro dynamický nebo modul v paměti.</span><span class="sxs-lookup"><span data-stu-id="94b86-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94b86-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94b86-112">Requirements</span></span>  
 <span data-ttu-id="94b86-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94b86-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94b86-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="94b86-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94b86-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94b86-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94b86-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94b86-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b86-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94b86-117">See also</span></span>
