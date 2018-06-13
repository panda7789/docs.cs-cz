---
title: ISymUnmanagedWriter::SetSymAttribute – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1a55d4100d74b769b2bc1b8fe33d2042f5e739
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428298"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="2cb59-102">ISymUnmanagedWriter::SetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="2cb59-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="2cb59-103">Definuje vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="2cb59-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="2cb59-104">Tyto atributy jsou uložené v úložiště symbolů, na rozdíl od vlastní atributy metadat.</span><span class="sxs-lookup"><span data-stu-id="2cb59-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb59-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cb59-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cb59-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cb59-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="2cb59-107">[v] Metadata token, pro který je definován atribut.</span><span class="sxs-lookup"><span data-stu-id="2cb59-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="2cb59-108">[v] Ukazatel na `WCHAR` obsahující název atributu.</span><span class="sxs-lookup"><span data-stu-id="2cb59-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="2cb59-109">[v] A `ULONG32` určující velikost `data` pole.</span><span class="sxs-lookup"><span data-stu-id="2cb59-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="2cb59-110">[v] Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="2cb59-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cb59-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2cb59-111">Return Value</span></span>  
 <span data-ttu-id="2cb59-112">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2cb59-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb59-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cb59-113">Requirements</span></span>  
 <span data-ttu-id="2cb59-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2cb59-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb59-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cb59-115">See Also</span></span>  
 [<span data-ttu-id="2cb59-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cb59-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
