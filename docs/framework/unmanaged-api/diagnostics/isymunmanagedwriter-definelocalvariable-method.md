---
title: ISymUnmanagedWriter::DefineLocalVariable – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: 5730cdd910257d762230f5e54576d5e0a7ac1adb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614822"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="4fd84-102">ISymUnmanagedWriter::DefineLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="4fd84-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="4fd84-103">Definuje jednu proměnnou v aktuálním lexikálním oboru.</span><span class="sxs-lookup"><span data-stu-id="4fd84-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="4fd84-104">Tuto metodu lze volat vícekrát pro proměnnou se stejným názvem, který má více obydlí v celém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4fd84-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="4fd84-105">V tomto případě se však hodnoty `startOffset` `endOffset` parametrů a nesmí překrývat.</span><span class="sxs-lookup"><span data-stu-id="4fd84-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd84-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fd84-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fd84-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fd84-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4fd84-108">pro Ukazatel na `WCHAR` , který definuje název místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="4fd84-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="4fd84-109">pro Atributy místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="4fd84-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="4fd84-110">pro `ULONG32`Který udává velikost vyrovnávací paměti v bajtech `signature` .</span><span class="sxs-lookup"><span data-stu-id="4fd84-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="4fd84-111">pro Lokální podpis proměnné.</span><span class="sxs-lookup"><span data-stu-id="4fd84-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="4fd84-112">pro Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="4fd84-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="4fd84-113">pro První adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="4fd84-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="4fd84-114">pro Druhá adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="4fd84-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="4fd84-115">pro Třetí adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="4fd84-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="4fd84-116">pro Počáteční posun pro proměnnou</span><span class="sxs-lookup"><span data-stu-id="4fd84-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="4fd84-117">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="4fd84-117">This parameter is optional.</span></span> <span data-ttu-id="4fd84-118">Pokud je 0, tento parametr je ignorován a proměnná je definována v celém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4fd84-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="4fd84-119">Pokud je to nenulová hodnota, proměnná spadá do posunu aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="4fd84-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="4fd84-120">pro Koncový posun proměnné</span><span class="sxs-lookup"><span data-stu-id="4fd84-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="4fd84-121">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="4fd84-121">This parameter is optional.</span></span> <span data-ttu-id="4fd84-122">Pokud je 0, tento parametr je ignorován a proměnná je definována v celém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4fd84-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="4fd84-123">Pokud je to nenulová hodnota, proměnná spadá do posunu aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="4fd84-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fd84-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4fd84-124">Return Value</span></span>  
 <span data-ttu-id="4fd84-125">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4fd84-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fd84-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fd84-126">Requirements</span></span>  
 <span data-ttu-id="4fd84-127">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4fd84-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd84-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fd84-128">See also</span></span>

- [<span data-ttu-id="4fd84-129">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fd84-129">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="4fd84-130">DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="4fd84-130">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="4fd84-131">DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4fd84-131">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)
