---
title: ICLRDataTarget::GetTLSValue – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: d4e7c055480ea611357d5d3e18ac4306acf4d0b0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785408"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="6ed4b-102">ICLRDataTarget::GetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="6ed4b-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="6ed4b-103">Získá hodnotu z thread local Storage (TLS) zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="6ed4b-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="6ed4b-104">Tato metoda je volána službou Common Language Runtime (CLR) pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="6ed4b-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed4b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed4b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ed4b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ed4b-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="6ed4b-107">pro Identifikátor operačního systému vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="6ed4b-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="6ed4b-108">pro Index umístění.</span><span class="sxs-lookup"><span data-stu-id="6ed4b-108">[in] The index of the location.</span></span> <span data-ttu-id="6ed4b-109">Tato hodnota musí být platný index v místním úložišti zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="6ed4b-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="6ed4b-110">mimo Ukazatel na hodnotu `CLRDATA_ADDRESS`, která určuje hodnotu vrácenou z daného umístění TLS.</span><span class="sxs-lookup"><span data-stu-id="6ed4b-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ed4b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ed4b-111">Remarks</span></span>  
 <span data-ttu-id="6ed4b-112">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ed4b-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed4b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ed4b-113">Requirements</span></span>  
 <span data-ttu-id="6ed4b-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed4b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed4b-115">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="6ed4b-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6ed4b-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6ed4b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ed4b-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed4b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed4b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ed4b-118">See also</span></span>

- [<span data-ttu-id="6ed4b-119">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ed4b-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
