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
ms.openlocfilehash: 52e1fc20fbe1d8709c21cacde926cf8bebb49425
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449199"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="e85aa-102">ISymUnmanagedDocument::GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="e85aa-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="e85aa-103">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="e85aa-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e85aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e85aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e85aa-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="e85aa-106">pro Délka vyrovnávací paměti poskytnuté parametrem `data`</span><span class="sxs-lookup"><span data-stu-id="e85aa-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="e85aa-107">mimo Velikost a délka kontrolního součtu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="e85aa-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="e85aa-108">mimo Vyrovnávací paměť, která přijímá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="e85aa-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e85aa-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e85aa-109">Return Value</span></span>  
 <span data-ttu-id="e85aa-110">S_OK, pokud je metoda úspěšná; v opačném případě kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e85aa-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85aa-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e85aa-111">See also</span></span>

- [<span data-ttu-id="e85aa-112">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e85aa-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
