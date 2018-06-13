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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71be697a8a1decd9b5f780d047c3dbb397e351d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426885"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="fea6e-102">ISymUnmanagedWriter::CloseMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="fea6e-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="fea6e-103">Zavře aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="fea6e-103">Closes the current method.</span></span> <span data-ttu-id="fea6e-104">Jakmile je uzavřený metodu, může být definováno žádné další symboly v něm.</span><span class="sxs-lookup"><span data-stu-id="fea6e-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fea6e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fea6e-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fea6e-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fea6e-106">Return Value</span></span>  
 <span data-ttu-id="fea6e-107">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fea6e-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fea6e-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fea6e-108">Requirements</span></span>  
 <span data-ttu-id="fea6e-109">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fea6e-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea6e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="fea6e-110">See Also</span></span>  
 [<span data-ttu-id="fea6e-111">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fea6e-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="fea6e-112">OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="fea6e-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
