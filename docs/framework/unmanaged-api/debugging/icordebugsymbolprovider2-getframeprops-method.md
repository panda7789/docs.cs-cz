---
title: 'ICorDebugSymbolProvider2:: GetFrameProps – metoda'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: 39bdb93fcb48da6667d982ca2d511ee5e499ae32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133647"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="1429a-102">ICorDebugSymbolProvider2:: GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="1429a-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="1429a-103">Vrátí metodu, která spouští relativní virtuální adresu metody a nadřazený rámec pro relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="1429a-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1429a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1429a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1429a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1429a-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="1429a-106">pro Relativní virtuální adresa pro kód.</span><span class="sxs-lookup"><span data-stu-id="1429a-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="1429a-107">mimo Ukazatel na počáteční relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="1429a-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="1429a-108">mimo Ukazatel na počáteční relativní virtuální adresu rámce.</span><span class="sxs-lookup"><span data-stu-id="1429a-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1429a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1429a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1429a-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1429a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1429a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1429a-111">Requirements</span></span>  
 <span data-ttu-id="1429a-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1429a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1429a-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1429a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1429a-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1429a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1429a-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1429a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1429a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1429a-116">See also</span></span>

- [<span data-ttu-id="1429a-117">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1429a-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="1429a-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1429a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
