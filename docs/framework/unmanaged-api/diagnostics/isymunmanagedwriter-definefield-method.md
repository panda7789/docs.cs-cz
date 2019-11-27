---
title: ISymUnmanagedWriter::DefineField – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 7eea63cae27c08260177dfc7746046b975434611
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428032"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="8c7c2-102">ISymUnmanagedWriter::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="8c7c2-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="8c7c2-103">Definuje jednu proměnnou, která není v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="8c7c2-104">Tato metoda se používá pro určitá pole ve třídách, bitových polích a tak dále.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c7c2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c7c2-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c7c2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c7c2-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="8c7c2-107">pro Typ metadat nebo token metody.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="8c7c2-108">pro Název pole</span><span class="sxs-lookup"><span data-stu-id="8c7c2-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="8c7c2-109">pro Atributy pole</span><span class="sxs-lookup"><span data-stu-id="8c7c2-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="8c7c2-110">pro `ULONG32`, která má velikost vyrovnávací paměti, která je nutná k omezení podpisu pole, ve znacích.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="8c7c2-111">pro Pole podpisů polí.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="8c7c2-112">pro Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="8c7c2-113">pro První adresa specifikace pole</span><span class="sxs-lookup"><span data-stu-id="8c7c2-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="8c7c2-114">pro Druhá adresa specifikace pole</span><span class="sxs-lookup"><span data-stu-id="8c7c2-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="8c7c2-115">pro Třetí adresa specifikace pole</span><span class="sxs-lookup"><span data-stu-id="8c7c2-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c7c2-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8c7c2-116">Return Value</span></span>  
 <span data-ttu-id="8c7c2-117">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c7c2-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c7c2-118">Requirements</span></span>  
 <span data-ttu-id="8c7c2-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8c7c2-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c7c2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c7c2-120">See also</span></span>

- [<span data-ttu-id="8c7c2-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c7c2-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
