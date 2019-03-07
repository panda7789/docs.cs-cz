---
title: ISymUnmanagedReader::GetMethodByVersion – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebf2fea9f987818c93a1e865f2ed2ce33142050c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468660"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="e91a6-102">ISymUnmanagedReader::GetMethodByVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="e91a6-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="e91a6-103">Získá metodu čtečky symbolů daný token metody a číslo verze upravit a kopírovat.</span><span class="sxs-lookup"><span data-stu-id="e91a6-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="e91a6-104">Čísla verzí začínají znakem 1 a jsou zvětšeny pokaždé, když metoda se změnilo v důsledku operace upravit a kopírovat.</span><span class="sxs-lookup"><span data-stu-id="e91a6-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91a6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e91a6-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e91a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e91a6-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="e91a6-107">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="e91a6-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="e91a6-108">[in] Metoda verze.</span><span class="sxs-lookup"><span data-stu-id="e91a6-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e91a6-109">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e91a6-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e91a6-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e91a6-110">Return Value</span></span>  
 <span data-ttu-id="e91a6-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e91a6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e91a6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e91a6-112">Requirements</span></span>  
 <span data-ttu-id="e91a6-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e91a6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91a6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e91a6-114">See also</span></span>
- [<span data-ttu-id="e91a6-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e91a6-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
