---
title: ISymUnmanagedWriter::UsingNamespace – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: e4348cc59924b65b6c6bb53a9c2a98f1a1161b50
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614731"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="24473-102">ISymUnmanagedWriter::UsingNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="24473-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="24473-103">Určuje, že zadaný plně kvalifikovaný název oboru názvů se používá v aktuálně otevřeném lexikálním oboru.</span><span class="sxs-lookup"><span data-stu-id="24473-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="24473-104">Obor názvů se použije ve všech oborech, které dědí z aktuálně otevřeného oboru.</span><span class="sxs-lookup"><span data-stu-id="24473-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="24473-105">Zavřením aktuálního oboru dojde také k zastavení použití oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="24473-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24473-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24473-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24473-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="24473-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="24473-108">pro Ukazatel na plně kvalifikovaný název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="24473-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24473-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="24473-109">Return Value</span></span>  
 <span data-ttu-id="24473-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="24473-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24473-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24473-111">Requirements</span></span>  
 <span data-ttu-id="24473-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="24473-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24473-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="24473-113">See also</span></span>

- [<span data-ttu-id="24473-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24473-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
