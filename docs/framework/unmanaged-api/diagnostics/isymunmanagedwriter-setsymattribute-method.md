---
title: "ISymUnmanagedWriter::SetSymAttribute – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c59c3c8ec4534f0a7587d4fdb772683715363066
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="2bc22-102">ISymUnmanagedWriter::SetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc22-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="2bc22-103">Definuje vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="2bc22-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="2bc22-104">Tyto atributy jsou uložené v úložiště symbolů, na rozdíl od vlastní atributy metadat.</span><span class="sxs-lookup"><span data-stu-id="2bc22-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc22-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bc22-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bc22-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bc22-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="2bc22-107">[v] Metadata token, pro který je definován atribut.</span><span class="sxs-lookup"><span data-stu-id="2bc22-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="2bc22-108">[v] Ukazatel na `WCHAR` obsahující název atributu.</span><span class="sxs-lookup"><span data-stu-id="2bc22-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="2bc22-109">[v] A `ULONG32` určující velikost `data` pole.</span><span class="sxs-lookup"><span data-stu-id="2bc22-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="2bc22-110">[v] Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="2bc22-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bc22-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2bc22-111">Return Value</span></span>  
 <span data-ttu-id="2bc22-112">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2bc22-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc22-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bc22-113">Requirements</span></span>  
 <span data-ttu-id="2bc22-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2bc22-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc22-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bc22-115">See Also</span></span>  
 [<span data-ttu-id="2bc22-116">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bc22-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
