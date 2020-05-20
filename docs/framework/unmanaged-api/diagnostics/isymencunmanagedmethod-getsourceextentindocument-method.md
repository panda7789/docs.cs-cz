---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 3ac8bb3a20ce82b734a572832a9cbb75fa2568c4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441900"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="abf74-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="abf74-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="abf74-103">Získá nejmenší počáteční řádek a největšího koncového řádku pro metodu v konkrétním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="abf74-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abf74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abf74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abf74-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="abf74-106">pro Ukazatel na dokument.</span><span class="sxs-lookup"><span data-stu-id="abf74-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="abf74-107">mimo Ukazatel na `ULONG32` , který obdrží počáteční řádek.</span><span class="sxs-lookup"><span data-stu-id="abf74-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="abf74-108">mimo Ukazatel na `ULONG32` , který získá koncovou čáru.</span><span class="sxs-lookup"><span data-stu-id="abf74-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abf74-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="abf74-109">Return Value</span></span>  
 <span data-ttu-id="abf74-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="abf74-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abf74-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abf74-111">Requirements</span></span>  
 <span data-ttu-id="abf74-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="abf74-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf74-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="abf74-113">See also</span></span>

- [<span data-ttu-id="abf74-114">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abf74-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
