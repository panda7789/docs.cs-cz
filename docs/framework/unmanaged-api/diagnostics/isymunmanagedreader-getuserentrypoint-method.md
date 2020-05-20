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
ms.openlocfilehash: d465f830fa73016c3cf3f7df3a4a4d0c42bc0980
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615498"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="69e04-102">ISymUnmanagedReader::GetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="69e04-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="69e04-103">Vrátí metodu, která byla zadána jako vstupní bod uživatele pro modul, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="69e04-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="69e04-104">Tato metoda může být například metoda Main uživatele, nikoli zástupné procedury generované kompilátorem před metodou Main.</span><span class="sxs-lookup"><span data-stu-id="69e04-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69e04-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69e04-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69e04-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="69e04-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="69e04-107">mimo Ukazatel na proměnnou, která přijímá vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="69e04-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69e04-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="69e04-108">Return Value</span></span>  
 <span data-ttu-id="69e04-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="69e04-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69e04-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69e04-110">Requirements</span></span>  
 <span data-ttu-id="69e04-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="69e04-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e04-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="69e04-112">See also</span></span>

- [<span data-ttu-id="69e04-113">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69e04-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
