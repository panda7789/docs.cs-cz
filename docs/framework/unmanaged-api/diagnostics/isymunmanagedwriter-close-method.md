---
title: ISymUnmanagedWriter::Close – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 0a7ecd475a8031fedb2c8474593b45045fcc6fb9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610129"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="db208-102">ISymUnmanagedWriter::Close – metoda</span><span class="sxs-lookup"><span data-stu-id="db208-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="db208-103">Po potvrzení symbolů do úložiště symbolů zavře zapisovač symbolů.</span><span class="sxs-lookup"><span data-stu-id="db208-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db208-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db208-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="db208-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db208-105">Return Value</span></span>  
 <span data-ttu-id="db208-106">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="db208-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db208-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db208-107">Remarks</span></span>  
 <span data-ttu-id="db208-108">Po tomto volání bude zapisovač symbolů pro další aktualizace neplatný.</span><span class="sxs-lookup"><span data-stu-id="db208-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="db208-109">Chcete-li zavřít zapisovač symbolů bez potvrzení symbolů, použijte místo toho metodu [ISymUnmanagedWriter:: Abort](isymunmanagedwriter-abort-method.md) .</span><span class="sxs-lookup"><span data-stu-id="db208-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db208-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db208-110">Requirements</span></span>  
 <span data-ttu-id="db208-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="db208-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db208-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="db208-112">See also</span></span>

- [<span data-ttu-id="db208-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db208-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
