---
title: ISymUnmanagedDispose::Destroy – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: 5bd94cb851d4bb044d4ce03b97d6342a2c9652e4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441315"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="ee1d7-102">ISymUnmanagedDispose::Destroy – metoda</span><span class="sxs-lookup"><span data-stu-id="ee1d7-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="ee1d7-103">Způsobí, že podkladový objekt uvolní všechny interní odkazy a vrátí chybu pro jakékoli následné volání metody.</span><span class="sxs-lookup"><span data-stu-id="ee1d7-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee1d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee1d7-104">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ee1d7-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ee1d7-105">Return Value</span></span>  
 <span data-ttu-id="ee1d7-106">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ee1d7-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee1d7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee1d7-107">Requirements</span></span>  
 <span data-ttu-id="ee1d7-108">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ee1d7-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1d7-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee1d7-109">See also</span></span>

- [<span data-ttu-id="ee1d7-110">ISymUnmanagedDispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee1d7-110">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
