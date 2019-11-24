---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
ms.openlocfilehash: a193c4e9e87616217efc90286032944d05d766c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446395"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="877c6-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="877c6-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="877c6-103">Gets a count of symbol search information.</span><span class="sxs-lookup"><span data-stu-id="877c6-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="877c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="877c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="877c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="877c6-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="877c6-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span><span class="sxs-lookup"><span data-stu-id="877c6-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="877c6-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="877c6-107">Return Value</span></span>  
 <span data-ttu-id="877c6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="877c6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="877c6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="877c6-109">Requirements</span></span>  
 <span data-ttu-id="877c6-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="877c6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877c6-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="877c6-111">See also</span></span>

- [<span data-ttu-id="877c6-112">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="877c6-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
