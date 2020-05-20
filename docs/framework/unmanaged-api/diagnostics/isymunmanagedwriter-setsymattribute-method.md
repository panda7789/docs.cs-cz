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
ms.openlocfilehash: 39b0c065a324f2b3939467901739f995bc9abbad
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614757"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="86f07-102">ISymUnmanagedWriter::SetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="86f07-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="86f07-103">Definuje vlastní atribut založený na jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="86f07-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="86f07-104">Tyto atributy jsou uloženy v úložišti symbolů na rozdíl od vlastních atributů metadat.</span><span class="sxs-lookup"><span data-stu-id="86f07-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f07-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86f07-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86f07-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="86f07-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="86f07-107">pro Token metadat, pro který je definován atribut.</span><span class="sxs-lookup"><span data-stu-id="86f07-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="86f07-108">pro Ukazatel na `WCHAR` , který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="86f07-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="86f07-109">pro `ULONG32`Který označuje velikost `data` pole.</span><span class="sxs-lookup"><span data-stu-id="86f07-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="86f07-110">pro Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="86f07-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86f07-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="86f07-111">Return Value</span></span>  
 <span data-ttu-id="86f07-112">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="86f07-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f07-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86f07-113">Requirements</span></span>  
 <span data-ttu-id="86f07-114">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="86f07-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f07-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="86f07-115">See also</span></span>

- [<span data-ttu-id="86f07-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86f07-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
