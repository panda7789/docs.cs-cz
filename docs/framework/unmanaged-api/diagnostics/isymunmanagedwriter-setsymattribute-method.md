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
ms.openlocfilehash: 8ffcc3a079e7e9a9d69622dc6666bb0e7641d4e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155464"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="069e4-102">ISymUnmanagedWriter::SetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="069e4-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="069e4-103">Definuje vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="069e4-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="069e4-104">Tyto atributy jsou uložené v úložišti symbolů, na rozdíl od vlastních atributů metadat.</span><span class="sxs-lookup"><span data-stu-id="069e4-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069e4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="069e4-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="069e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="069e4-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="069e4-107">[in] Token metadat, pro který je definován atribut.</span><span class="sxs-lookup"><span data-stu-id="069e4-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="069e4-108">[in] Ukazatel `WCHAR` , který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="069e4-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="069e4-109">[in] A `ULONG32` , který označuje velikost `data` pole.</span><span class="sxs-lookup"><span data-stu-id="069e4-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="069e4-110">[in] Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="069e4-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="069e4-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="069e4-111">Return Value</span></span>  
 <span data-ttu-id="069e4-112">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="069e4-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="069e4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="069e4-113">Requirements</span></span>  
 <span data-ttu-id="069e4-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="069e4-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069e4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="069e4-115">See also</span></span>

- [<span data-ttu-id="069e4-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="069e4-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
