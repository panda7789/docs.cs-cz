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
ms.openlocfilehash: 4450c262b75a73114cb7de7de98567f053bbf564
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894463"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="47529-102">ISymUnmanagedWriter::SetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="47529-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="47529-103">Definuje vlastní atribut založený na jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="47529-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="47529-104">Tyto atributy jsou uloženy v úložišti symbolů na rozdíl od vlastních atributů metadat.</span><span class="sxs-lookup"><span data-stu-id="47529-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47529-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47529-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47529-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="47529-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="47529-107">pro Token metadat, pro který je definován atribut.</span><span class="sxs-lookup"><span data-stu-id="47529-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="47529-108">pro Ukazatel na `WCHAR` , který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="47529-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="47529-109">pro Který označuje velikost `data`pole. `ULONG32`</span><span class="sxs-lookup"><span data-stu-id="47529-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="47529-110">pro Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="47529-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47529-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="47529-111">Return Value</span></span>  
 <span data-ttu-id="47529-112">S_OK, pokud je metoda úspěšná; jinak E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="47529-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47529-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47529-113">Requirements</span></span>  
 <span data-ttu-id="47529-114">**Hlaviček** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="47529-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47529-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47529-115">See also</span></span>

- [<span data-ttu-id="47529-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47529-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
