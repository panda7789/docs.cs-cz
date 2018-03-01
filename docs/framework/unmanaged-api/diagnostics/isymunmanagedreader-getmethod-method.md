---
title: "ISymUnmanagedReader::GetMethod – metoda"
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
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7af3f56bc258ba48abba5cba4230de3ca6904ec0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="638bd-102">ISymUnmanagedReader::GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="638bd-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="638bd-103">Získá metody čtečky symbol, zadaný token metoda.</span><span class="sxs-lookup"><span data-stu-id="638bd-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="638bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="638bd-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="638bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="638bd-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="638bd-106">[v] Metoda token.</span><span class="sxs-lookup"><span data-stu-id="638bd-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="638bd-107">[out] Ukazatel rozhraní vrácená.</span><span class="sxs-lookup"><span data-stu-id="638bd-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="638bd-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="638bd-108">Return Value</span></span>  
 <span data-ttu-id="638bd-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="638bd-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="638bd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="638bd-110">Requirements</span></span>  
 <span data-ttu-id="638bd-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="638bd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638bd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="638bd-112">See Also</span></span>  
 [<span data-ttu-id="638bd-113">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="638bd-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
