---
title: "ISymUnmanagedReader2::GetSymAttributePreRemap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetSymAttributePreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75608d89b6fd34570166718de824150b0621c84e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="de65a-102">ISymUnmanagedReader2::GetSymAttributePreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="de65a-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="de65a-103">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="de65a-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="de65a-104">Na rozdíl od metadata vlastní atributy jsou tyto atributy uložené v úložišti symbol.</span><span class="sxs-lookup"><span data-stu-id="de65a-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de65a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de65a-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de65a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="de65a-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="de65a-107">[v] Metadata token nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="de65a-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="de65a-108">[v] Ukazatel na `WCHAR` obsahující název.</span><span class="sxs-lookup"><span data-stu-id="de65a-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="de65a-109">[v] A `ULONG32` určující velikost `buffer` pole.</span><span class="sxs-lookup"><span data-stu-id="de65a-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="de65a-110">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat atribut bajtů.</span><span class="sxs-lookup"><span data-stu-id="de65a-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="de65a-111">[out] Ukazatel na vyrovnávací paměť, která obdrží atribut bajtů.</span><span class="sxs-lookup"><span data-stu-id="de65a-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de65a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="de65a-112">Return Value</span></span>  
 <span data-ttu-id="de65a-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="de65a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de65a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de65a-114">Requirements</span></span>  
 <span data-ttu-id="de65a-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="de65a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de65a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="de65a-116">See Also</span></span>  
 [<span data-ttu-id="de65a-117">Isymunmanagedreader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de65a-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
