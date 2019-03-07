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
ms.openlocfilehash: ea0cba1f1b9154ccb14d75f7c377a8153c24f2b0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499475"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="7ce11-102">ISymUnmanagedReader::GetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="7ce11-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="7ce11-103">Vrátí metodu, která byla zadána jako uživatel vstupní bod pro modul, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="7ce11-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="7ce11-104">Tato metoda může být například hlavní metoda uživatele spíše než vygenerovaný kompilátorem zástupné procedury před voláním hlavní metody.</span><span class="sxs-lookup"><span data-stu-id="7ce11-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce11-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ce11-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ce11-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ce11-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="7ce11-107">[out] Ukazovat na proměnnou, která přijímá vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="7ce11-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ce11-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7ce11-108">Return Value</span></span>  
 <span data-ttu-id="7ce11-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7ce11-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ce11-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ce11-110">Requirements</span></span>  
 <span data-ttu-id="7ce11-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ce11-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce11-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ce11-112">See also</span></span>
- [<span data-ttu-id="7ce11-113">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ce11-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
