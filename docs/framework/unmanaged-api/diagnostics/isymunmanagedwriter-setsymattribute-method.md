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
ms.openlocfilehash: 8a4d205586921b377147eeab80754e1a0d9e52b0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427838"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="6a889-102">ISymUnmanagedWriter::SetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="6a889-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="6a889-103">Definuje vlastní atribut založený na jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="6a889-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="6a889-104">Tyto atributy jsou uloženy v úložišti symbolů na rozdíl od vlastních atributů metadat.</span><span class="sxs-lookup"><span data-stu-id="6a889-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a889-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a889-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a889-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a889-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="6a889-107">pro Token metadat, pro který je definován atribut.</span><span class="sxs-lookup"><span data-stu-id="6a889-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="6a889-108">pro Ukazatel na `WCHAR`, který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="6a889-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="6a889-109">pro `ULONG32`, která určuje velikost `data` pole.</span><span class="sxs-lookup"><span data-stu-id="6a889-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="6a889-110">pro Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="6a889-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a889-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a889-111">Return Value</span></span>  
 <span data-ttu-id="6a889-112">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6a889-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a889-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a889-113">Requirements</span></span>  
 <span data-ttu-id="6a889-114">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6a889-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a889-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a889-115">See also</span></span>

- [<span data-ttu-id="6a889-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a889-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
