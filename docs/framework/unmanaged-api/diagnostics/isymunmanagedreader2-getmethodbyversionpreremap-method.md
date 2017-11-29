---
title: "ISymUnmanagedReader2::GetMethodByVersionPreRemap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 69a203424320a176cd285c23d98111e71709042a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="1b202-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="1b202-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="1b202-103">Získá metody čtečky symbol, zadaný token metoda a čísla verze upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="1b202-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="1b202-104">Čísla verzí začínají znakem 1 a je zvýšen pokaždé, když metoda mění v důsledku operace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="1b202-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b202-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b202-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b202-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b202-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="1b202-107">[v] Metoda token metadat.</span><span class="sxs-lookup"><span data-stu-id="1b202-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="1b202-108">[v] Metoda verze.</span><span class="sxs-lookup"><span data-stu-id="1b202-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1b202-109">[out] Ukazatel na vrácený [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b202-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b202-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1b202-110">Return Value</span></span>  
 <span data-ttu-id="1b202-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1b202-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b202-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b202-112">Requirements</span></span>  
 <span data-ttu-id="1b202-113">**Záhlaví:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="1b202-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="1b202-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1b202-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b202-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b202-115">See Also</span></span>  
 [<span data-ttu-id="1b202-116">Isymunmanagedreader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b202-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
