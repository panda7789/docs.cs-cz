---
title: 'ICorDebugSymbolProvider:: Getmethodprops – – metoda'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 58642d0a9b1cfe1fd969f39fa7e5ab22a8dbfa05
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791583"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="0a5b1-102">ICorDebugSymbolProvider:: Getmethodprops – – metoda</span><span class="sxs-lookup"><span data-stu-id="0a5b1-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="0a5b1-103">Vrátí informace o vlastnostech metody, jako je token metadat metody a informace o jeho obecných parametrech, s ohledem na relativní virtuální adresu (RVA) v této metodě.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a5b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a5b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a5b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a5b1-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="0a5b1-106">pro Relativní virtuální adresa v metodě, o které se mají načíst informace</span><span class="sxs-lookup"><span data-stu-id="0a5b1-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="0a5b1-107">mimo Ukazatel na token metadat metody.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="0a5b1-108">mimo Ukazatel na počet obecných parametrů přidružených k této metodě.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="0a5b1-109">pro Velikost pole `signature`.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="0a5b1-110">Viz část poznámky.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="0a5b1-111">mimo Ukazatel na velikost vráceného pole `signature`.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="0a5b1-112">mimo Vyrovnávací paměť, která obsahuje token TypeSpec podpisy všech obecných parametrů.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a5b1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a5b1-113">Remarks</span></span>  
 <span data-ttu-id="0a5b1-114">Chcete-li získat požadovanou velikost `signature` pole metody, nastavte argument `cbSignature` na hodnotu 0 a `signature` na **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="0a5b1-115">Když se metoda vrátí, `pcbSignature` bude obsahovat počet bajtů vyžadovaných pro pole `signature`.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a5b1-116">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0a5b1-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a5b1-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a5b1-117">Requirements</span></span>  
 <span data-ttu-id="0a5b1-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a5b1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a5b1-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0a5b1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a5b1-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0a5b1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a5b1-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a5b1-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a5b1-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a5b1-122">See also</span></span>

- [<span data-ttu-id="0a5b1-123">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0a5b1-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="0a5b1-124">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a5b1-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="0a5b1-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0a5b1-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
