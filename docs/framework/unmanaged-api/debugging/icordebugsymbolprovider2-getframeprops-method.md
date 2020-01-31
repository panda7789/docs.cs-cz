---
title: 'ICorDebugSymbolProvider2:: GetFrameProps – metoda'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: dc64152938c46945978715251286ecb6c6d8983c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791513"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="19968-102">ICorDebugSymbolProvider2:: GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="19968-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="19968-103">Vrátí metodu, která spouští relativní virtuální adresu metody a nadřazený rámec pro relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="19968-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19968-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19968-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19968-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19968-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="19968-106">pro Relativní virtuální adresa pro kód.</span><span class="sxs-lookup"><span data-stu-id="19968-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="19968-107">mimo Ukazatel na počáteční relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="19968-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="19968-108">mimo Ukazatel na počáteční relativní virtuální adresu rámce.</span><span class="sxs-lookup"><span data-stu-id="19968-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19968-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19968-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19968-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="19968-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19968-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19968-111">Requirements</span></span>  
 <span data-ttu-id="19968-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19968-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19968-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19968-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19968-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="19968-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19968-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19968-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19968-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19968-116">See also</span></span>

- [<span data-ttu-id="19968-117">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19968-117">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="19968-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="19968-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
