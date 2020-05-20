---
title: ISymUnmanagedWriter::DefineConstant – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
ms.openlocfilehash: 200e68abb3f176c267045bf2a5e7e35d18400519
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610090"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="228e5-102">ISymUnmanagedWriter::DefineConstant – metoda</span><span class="sxs-lookup"><span data-stu-id="228e5-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="228e5-103">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="228e5-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="228e5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="228e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="228e5-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="228e5-106">pro Ukazatel na `WCHAR` , který definuje název konstanty.</span><span class="sxs-lookup"><span data-stu-id="228e5-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="228e5-107">pro Hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="228e5-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="228e5-108">pro Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="228e5-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="228e5-109">pro Podpis typu konstanty.</span><span class="sxs-lookup"><span data-stu-id="228e5-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="228e5-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="228e5-110">Return Value</span></span>  
 <span data-ttu-id="228e5-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="228e5-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="228e5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="228e5-112">Requirements</span></span>  
 <span data-ttu-id="228e5-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="228e5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228e5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="228e5-114">See also</span></span>

- [<span data-ttu-id="228e5-115">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="228e5-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="228e5-116">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="228e5-116">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)
