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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b34f985f199542612bcdb9b30ebae28649438e1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776766"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="d6b48-102">ISymUnmanagedDocument::GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="d6b48-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="d6b48-103">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="d6b48-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b48-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6b48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6b48-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="d6b48-106">[in] Délka vyrovnávací paměti poskytované `data` parametr</span><span class="sxs-lookup"><span data-stu-id="d6b48-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="d6b48-107">[out] Velikost a délce kontrolní součet v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d6b48-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="d6b48-108">[out] Vyrovnávací paměť, která přijímá kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="d6b48-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6b48-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6b48-109">Return Value</span></span>  
 <span data-ttu-id="d6b48-110">Pokud metoda uspěje; S_OK v opačném případě chybový kód.</span><span class="sxs-lookup"><span data-stu-id="d6b48-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b48-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6b48-111">See also</span></span>

- [<span data-ttu-id="d6b48-112">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6b48-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
