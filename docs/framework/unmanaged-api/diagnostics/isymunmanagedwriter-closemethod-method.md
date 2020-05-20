---
title: ISymUnmanagedWriter::CloseMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
ms.openlocfilehash: fdf24bb8533da7914128f9477987c427442383bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610116"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="3adc8-102">ISymUnmanagedWriter::CloseMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="3adc8-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="3adc8-103">Zavře aktuální metodu.</span><span class="sxs-lookup"><span data-stu-id="3adc8-103">Closes the current method.</span></span> <span data-ttu-id="3adc8-104">Po uzavření metody nelze v ní definovat žádné další symboly.</span><span class="sxs-lookup"><span data-stu-id="3adc8-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3adc8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3adc8-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3adc8-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3adc8-106">Return Value</span></span>  
 <span data-ttu-id="3adc8-107">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3adc8-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3adc8-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3adc8-108">Requirements</span></span>  
 <span data-ttu-id="3adc8-109">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3adc8-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3adc8-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3adc8-110">See also</span></span>

- [<span data-ttu-id="3adc8-111">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3adc8-111">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="3adc8-112">OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="3adc8-112">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
