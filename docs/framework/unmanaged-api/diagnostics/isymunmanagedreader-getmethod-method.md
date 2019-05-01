---
title: ISymUnmanagedReader::GetMethod – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab6228866434b35525b16e97b8cba718b849dea1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993340"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="9c44e-102">ISymUnmanagedReader::GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="9c44e-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="9c44e-103">Získá metodu čtečky symbolů daný token metody.</span><span class="sxs-lookup"><span data-stu-id="9c44e-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c44e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c44e-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c44e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c44e-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="9c44e-106">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="9c44e-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9c44e-107">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9c44e-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c44e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9c44e-108">Return Value</span></span>  
 <span data-ttu-id="9c44e-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9c44e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c44e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c44e-110">Requirements</span></span>  
 <span data-ttu-id="9c44e-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9c44e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c44e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c44e-112">See also</span></span>

- [<span data-ttu-id="9c44e-113">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c44e-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
