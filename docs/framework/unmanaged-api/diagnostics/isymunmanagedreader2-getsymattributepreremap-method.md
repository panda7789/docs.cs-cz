---
title: ISymUnmanagedReader2::GetSymAttributePreRemap – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d5702f5df1e2d31a4e01de6be7c70af03b54296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519681"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="013ae-102">ISymUnmanagedReader2::GetSymAttributePreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="013ae-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="013ae-103">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="013ae-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="013ae-104">Na rozdíl od vlastních atributů metadat tyto atributy jsou uložené v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="013ae-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="013ae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="013ae-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="013ae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="013ae-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="013ae-107">[in] Token metadat nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="013ae-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="013ae-108">[in] Ukazatel `WCHAR` , který obsahuje název.</span><span class="sxs-lookup"><span data-stu-id="013ae-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="013ae-109">[in] A `ULONG32` , který označuje velikost `buffer` pole.</span><span class="sxs-lookup"><span data-stu-id="013ae-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="013ae-110">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat atribut bajtů.</span><span class="sxs-lookup"><span data-stu-id="013ae-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="013ae-111">[out] Ukazatel do vyrovnávací paměti, který přijímá atribut bajtů.</span><span class="sxs-lookup"><span data-stu-id="013ae-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="013ae-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="013ae-112">Return Value</span></span>  
 <span data-ttu-id="013ae-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="013ae-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="013ae-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="013ae-114">Requirements</span></span>  
 <span data-ttu-id="013ae-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="013ae-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013ae-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="013ae-116">See also</span></span>
- [<span data-ttu-id="013ae-117">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="013ae-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
