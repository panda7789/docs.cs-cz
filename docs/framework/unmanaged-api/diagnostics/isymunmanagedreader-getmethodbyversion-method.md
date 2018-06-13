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
ms.openlocfilehash: ef5888c33e9532e5fc132fe571d59699d6f80c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425168"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="fa3a3-102">ISymUnmanagedReader::GetMethodByVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="fa3a3-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="fa3a3-103">Získá metody čtečky symbol, zadaný token metoda a čísla verze úpravy a kopie.</span><span class="sxs-lookup"><span data-stu-id="fa3a3-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="fa3a3-104">Čísla verzí začínají znakem 1 a je zvýšen pokaždé, když metoda mění v důsledku operace upravit a kopie.</span><span class="sxs-lookup"><span data-stu-id="fa3a3-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa3a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa3a3-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa3a3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa3a3-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="fa3a3-107">[v] Metoda token.</span><span class="sxs-lookup"><span data-stu-id="fa3a3-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="fa3a3-108">[v] Metoda verze.</span><span class="sxs-lookup"><span data-stu-id="fa3a3-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="fa3a3-109">[out] Ukazatel rozhraní vrácená.</span><span class="sxs-lookup"><span data-stu-id="fa3a3-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa3a3-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fa3a3-110">Return Value</span></span>  
 <span data-ttu-id="fa3a3-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fa3a3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa3a3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa3a3-112">Requirements</span></span>  
 <span data-ttu-id="fa3a3-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fa3a3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa3a3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa3a3-114">See Also</span></span>  
 [<span data-ttu-id="fa3a3-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa3a3-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
