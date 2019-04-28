---
title: ISymUnmanagedReader::GetUserEntryPoint – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0267ae8b57c837b097d496c8e119085d03417e36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670024"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="548e4-102">ISymUnmanagedReader::GetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="548e4-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="548e4-103">Vrátí metodu, která byla zadána jako uživatel vstupní bod pro modul, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="548e4-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="548e4-104">Tato metoda může být například hlavní metoda uživatele spíše než vygenerovaný kompilátorem zástupné procedury před voláním hlavní metody.</span><span class="sxs-lookup"><span data-stu-id="548e4-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="548e4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="548e4-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="548e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="548e4-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="548e4-107">[out] Ukazovat na proměnnou, která přijímá vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="548e4-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="548e4-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="548e4-108">Return Value</span></span>  
 <span data-ttu-id="548e4-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="548e4-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="548e4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="548e4-110">Requirements</span></span>  
 <span data-ttu-id="548e4-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="548e4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548e4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="548e4-112">See also</span></span>

- [<span data-ttu-id="548e4-113">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="548e4-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
