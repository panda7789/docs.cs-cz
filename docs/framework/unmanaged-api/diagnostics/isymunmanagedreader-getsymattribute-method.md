---
title: "ISymUnmanagedReader::GetSymAttribute – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9795d5c7937f3c66c799665ba0e07e70c2be0b66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="45519-102">ISymUnmanagedReader::GetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="45519-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="45519-103">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="45519-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="45519-104">Na rozdíl od metadata vlastní atributy jsou tyto vlastní atributy uložené v úložišti symbol.</span><span class="sxs-lookup"><span data-stu-id="45519-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45519-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45519-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45519-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="45519-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="45519-107">[v] Token metadata pro objekt, pro který je požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="45519-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="45519-108">[v] Ukazatel na proměnnou, která určuje atribut, který se načíst.</span><span class="sxs-lookup"><span data-stu-id="45519-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="45519-109">[v] Velikost `buffer` pole.</span><span class="sxs-lookup"><span data-stu-id="45519-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="45519-110">[out] Ukazatel na proměnnou, která přijímá délka data atributu.</span><span class="sxs-lookup"><span data-stu-id="45519-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="45519-111">[out] Ukazatel na proměnnou, která přijímá data atributu.</span><span class="sxs-lookup"><span data-stu-id="45519-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45519-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="45519-112">Return Value</span></span>  
 <span data-ttu-id="45519-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby...</span><span class="sxs-lookup"><span data-stu-id="45519-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code..</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45519-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45519-114">Requirements</span></span>  
 <span data-ttu-id="45519-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="45519-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45519-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="45519-116">See Also</span></span>  
 [<span data-ttu-id="45519-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45519-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
