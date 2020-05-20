---
title: ISymUnmanagedMethod::GetSourceStartEnd – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 25e797fdf563a01ab727f16e7173eec2552eeb27
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614419"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="2d33b-102">ISymUnmanagedMethod::GetSourceStartEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="2d33b-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="2d33b-103">Získá pozice počátečního a koncového dokumentu pro zdroj této metody.</span><span class="sxs-lookup"><span data-stu-id="2d33b-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="2d33b-104">První pozice pole je začátek a druhá pozice pole je konec.</span><span class="sxs-lookup"><span data-stu-id="2d33b-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d33b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d33b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d33b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d33b-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="2d33b-107">pro Počáteční a koncové zdrojové dokumenty.</span><span class="sxs-lookup"><span data-stu-id="2d33b-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="2d33b-108">pro Počáteční a koncové řádky v odpovídajících zdrojových dokumentech.</span><span class="sxs-lookup"><span data-stu-id="2d33b-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="2d33b-109">pro Počáteční a koncové sloupce v odpovídajících zdrojových dokumentech.</span><span class="sxs-lookup"><span data-stu-id="2d33b-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2d33b-110">[out] `true` Pokud byly definovány pozice; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="2d33b-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d33b-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d33b-111">Return Value</span></span>  
 <span data-ttu-id="2d33b-112">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2d33b-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d33b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d33b-113">Requirements</span></span>  
 <span data-ttu-id="2d33b-114">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2d33b-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d33b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d33b-115">See also</span></span>

- [<span data-ttu-id="2d33b-116">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d33b-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
