---
title: ISymENCUnmanagedMethod::GetLineFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: d9a7b18e90a3038c1ffb634ccc7315143875c809
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441913"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="05947-102">ISymENCUnmanagedMethod::GetLineFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="05947-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="05947-103">Získá informace o řádku přidružené k posunu.</span><span class="sxs-lookup"><span data-stu-id="05947-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="05947-104">Pokud parametr offset ( `dwOffset` ) není bodem sekvence, tato metoda získá informace o řádku přidružené k předchozímu posunu.</span><span class="sxs-lookup"><span data-stu-id="05947-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05947-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05947-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05947-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="05947-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="05947-107">pro `ULONG32`, Který obsahuje posun.</span><span class="sxs-lookup"><span data-stu-id="05947-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="05947-108">mimo Ukazatel `ULONG32` , který získá řádek.</span><span class="sxs-lookup"><span data-stu-id="05947-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="05947-109">mimo Ukazatel na `ULONG32` , který přijímá sloupec.</span><span class="sxs-lookup"><span data-stu-id="05947-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="05947-110">mimo Ukazatel na `ULONG32` , který získá koncovou čáru.</span><span class="sxs-lookup"><span data-stu-id="05947-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="05947-111">mimo Ukazatel na `ULONG32` , který získá sloupec end.</span><span class="sxs-lookup"><span data-stu-id="05947-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="05947-112">mimo Ukazatel na `ULONG32` , který obdrží přidružený bod sekvence.</span><span class="sxs-lookup"><span data-stu-id="05947-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05947-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="05947-113">Return Value</span></span>  
 <span data-ttu-id="05947-114">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="05947-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05947-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05947-115">Requirements</span></span>  
 <span data-ttu-id="05947-116">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="05947-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05947-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="05947-117">See also</span></span>

- [<span data-ttu-id="05947-118">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05947-118">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
