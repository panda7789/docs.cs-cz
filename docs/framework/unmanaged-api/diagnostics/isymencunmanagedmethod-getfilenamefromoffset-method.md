---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 857410187edf1c712865626a3327dd4c92cc211f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441926"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="4a11e-102">ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="4a11e-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="4a11e-103">Získá název souboru pro řádek přidružený k posunu.</span><span class="sxs-lookup"><span data-stu-id="4a11e-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a11e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a11e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a11e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a11e-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="4a11e-106">pro `ULONG32`, Který obsahuje posun.</span><span class="sxs-lookup"><span data-stu-id="4a11e-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4a11e-107">pro `ULONG32`Který označuje velikost `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4a11e-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4a11e-108">mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k uložení názvů souborů.</span><span class="sxs-lookup"><span data-stu-id="4a11e-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="4a11e-109">mimo Vyrovnávací paměť, která obsahuje názvy souborů.</span><span class="sxs-lookup"><span data-stu-id="4a11e-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a11e-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4a11e-110">Return Value</span></span>  
 <span data-ttu-id="4a11e-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4a11e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a11e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a11e-112">Requirements</span></span>  
 <span data-ttu-id="4a11e-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4a11e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a11e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a11e-114">See also</span></span>

- [<span data-ttu-id="4a11e-115">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a11e-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
