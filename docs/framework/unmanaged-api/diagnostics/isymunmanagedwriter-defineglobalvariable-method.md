---
title: ISymUnmanagedWriter::DefineGlobalVariable – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: 674089f8a1076342a2479c64e253b7dda53ade87
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615199"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="bc444-102">ISymUnmanagedWriter::DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="bc444-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="bc444-103">Definuje jednu globální proměnnou.</span><span class="sxs-lookup"><span data-stu-id="bc444-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc444-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc444-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc444-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc444-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="bc444-106">pro Ukazatel na `WCHAR` , který definuje název globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="bc444-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="bc444-107">pro Atributy globálních proměnných.</span><span class="sxs-lookup"><span data-stu-id="bc444-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="bc444-108">pro `ULONG32`Který označuje velikost `signature` vyrovnávací paměti ve znacích.</span><span class="sxs-lookup"><span data-stu-id="bc444-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="bc444-109">pro Globální proměnná signatura</span><span class="sxs-lookup"><span data-stu-id="bc444-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="bc444-110">pro Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="bc444-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="bc444-111">pro První adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="bc444-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="bc444-112">pro Druhá adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="bc444-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="bc444-113">pro Třetí adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="bc444-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc444-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bc444-114">Return Value</span></span>  
 <span data-ttu-id="bc444-115">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="bc444-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc444-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc444-116">Requirements</span></span>  
 <span data-ttu-id="bc444-117">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bc444-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc444-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc444-118">See also</span></span>

- [<span data-ttu-id="bc444-119">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc444-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="bc444-120">DefineLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="bc444-120">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="bc444-121">DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="bc444-121">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
