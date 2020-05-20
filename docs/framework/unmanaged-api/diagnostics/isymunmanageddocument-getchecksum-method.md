---
title: ISymUnmanagedDocument::GetCheckSum – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 543bd208e5492460435663c32f276472a763f613
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441094"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="cf219-102">ISymUnmanagedDocument::GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="cf219-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="cf219-103">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="cf219-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf219-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf219-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf219-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf219-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="cf219-106">pro Délka vyrovnávací paměti poskytnuté `data` parametrem</span><span class="sxs-lookup"><span data-stu-id="cf219-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="cf219-107">mimo Velikost a délka kontrolního součtu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="cf219-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="cf219-108">mimo Vyrovnávací paměť, která přijímá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="cf219-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf219-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cf219-109">Return Value</span></span>  
 <span data-ttu-id="cf219-110">S_OK, pokud je metoda úspěšná; v opačném případě kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cf219-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf219-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf219-111">See also</span></span>

- [<span data-ttu-id="cf219-112">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf219-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
