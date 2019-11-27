---
title: ISymUnmanagedReader2::GetMethodsInDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
ms.openlocfilehash: 70c1d87ae32fb70f8d9f6e32b527394022459526
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446428"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="e825b-102">ISymUnmanagedReader2::GetMethodsInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="e825b-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="e825b-103">Načte každou metodu, která obsahuje informace o řádku v zadaném dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e825b-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e825b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e825b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e825b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e825b-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="e825b-106">pro Ukazatel na dokument.</span><span class="sxs-lookup"><span data-stu-id="e825b-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="e825b-107">pro `ULONG32`, která určuje velikost `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="e825b-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="e825b-108">mimo Ukazatel na `ULONG32`, který přijímá velikost vyrovnávací paměti, která je nutná k uložení metod.</span><span class="sxs-lookup"><span data-stu-id="e825b-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e825b-109">mimo Ukazatel na vyrovnávací paměť, která přijímá metody.</span><span class="sxs-lookup"><span data-stu-id="e825b-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e825b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e825b-110">Return Value</span></span>  
 <span data-ttu-id="e825b-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e825b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e825b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e825b-112">Requirements</span></span>  
 <span data-ttu-id="e825b-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e825b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e825b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e825b-114">See also</span></span>

- [<span data-ttu-id="e825b-115">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e825b-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
