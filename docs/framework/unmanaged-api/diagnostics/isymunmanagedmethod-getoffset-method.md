---
title: ISymUnmanagedMethod::GetOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: 358f3d3d7c231a2baa9d2c467935ba3a5867e36b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614471"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="d552f-102">ISymUnmanagedMethod::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="d552f-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="d552f-103">Vrátí posun v rámci této metody, který odpovídá dané pozici v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d552f-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d552f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d552f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d552f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d552f-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="d552f-106">pro Ukazatel na dokument, pro který je požadován posun.</span><span class="sxs-lookup"><span data-stu-id="d552f-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="d552f-107">pro Řádek dokumentu, pro který je požadován posun.</span><span class="sxs-lookup"><span data-stu-id="d552f-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="d552f-108">pro Sloupec dokumentu, pro který je požadován posun.</span><span class="sxs-lookup"><span data-stu-id="d552f-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d552f-109">mimo Ukazatel na `ULONG32` , který přijímá posuny.</span><span class="sxs-lookup"><span data-stu-id="d552f-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d552f-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d552f-110">Return Value</span></span>  
 <span data-ttu-id="d552f-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d552f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d552f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d552f-112">Requirements</span></span>  
 <span data-ttu-id="d552f-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d552f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d552f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d552f-114">See also</span></span>

- [<span data-ttu-id="d552f-115">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d552f-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
