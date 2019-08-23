---
title: 'ICorDebugSymbolProvider2:: GetFrameProps – metoda'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22e9c58a203c13611298e1956a6951d8ca7e8b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955499"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="6acf7-102">ICorDebugSymbolProvider2:: GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="6acf7-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="6acf7-103">Vrátí metodu, která spouští relativní virtuální adresu metody a nadřazený rámec pro relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="6acf7-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6acf7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6acf7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6acf7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6acf7-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="6acf7-106">pro Relativní virtuální adresa pro kód.</span><span class="sxs-lookup"><span data-stu-id="6acf7-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="6acf7-107">mimo Ukazatel na počáteční relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="6acf7-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="6acf7-108">mimo Ukazatel na počáteční relativní virtuální adresu rámce.</span><span class="sxs-lookup"><span data-stu-id="6acf7-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6acf7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6acf7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6acf7-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6acf7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6acf7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6acf7-111">Requirements</span></span>  
 <span data-ttu-id="6acf7-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6acf7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6acf7-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6acf7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6acf7-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6acf7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6acf7-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6acf7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6acf7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6acf7-116">See also</span></span>

- [<span data-ttu-id="6acf7-117">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6acf7-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="6acf7-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6acf7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
