---
title: ISymUnmanagedWriter::GetDebugInfo – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1e9a2261ab5fd06e0514efdddf8a8e952a6e3d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426893"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="6be73-102">ISymUnmanagedWriter::GetDebugInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="6be73-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="6be73-103">Vrací informace potřebné pro kompilátor zapsat záznam adresáře ladění přenosné hlavičky spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="6be73-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="6be73-104">Zapisovač symbol vyplní všechna pole s výjimkou `TimeDateStamp` a `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="6be73-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="6be73-105">(Kompilátor je zodpovědná za správně nastavení těchto dvou polích.)</span><span class="sxs-lookup"><span data-stu-id="6be73-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="6be73-106">Kompilátor by měly volat tuto metodu, emitování datový objekt blob do souboru PE, nastavte `PointerToRawData` pole IMAGE_DEBUG_DIRECTORY přejděte emitovaného data a IMAGE_DEBUG_DIRECTORY k zápisu do souboru PE.</span><span class="sxs-lookup"><span data-stu-id="6be73-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="6be73-107">Kompilátor nastavte také `TimeDateStamp` pole, aby se rovnala `TimeDateStamp` souboru PE generován.</span><span class="sxs-lookup"><span data-stu-id="6be73-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6be73-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6be73-108">Syntax</span></span>  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6be73-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="6be73-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="6be73-110">[ve out] Ukazatel IMAGE_DEBUG_DIRECTORY, který vyplní zapisovače symbol.</span><span class="sxs-lookup"><span data-stu-id="6be73-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="6be73-111">[v] A `DWORD` obsahující velikost dat ladění.</span><span class="sxs-lookup"><span data-stu-id="6be73-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="6be73-112">[out] Ukazatel na `DWORD` která přijme velikost vyrovnávací paměti musí obsahovat data ladění.</span><span class="sxs-lookup"><span data-stu-id="6be73-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="6be73-113">[out] Ukazatel na vyrovnávací paměť, která je dostatečně velký pro uložení dat ladění pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="6be73-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6be73-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6be73-114">Return Value</span></span>  
 <span data-ttu-id="6be73-115">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6be73-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6be73-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6be73-116">Requirements</span></span>  
 <span data-ttu-id="6be73-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6be73-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be73-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6be73-118">See Also</span></span>  
 [<span data-ttu-id="6be73-119">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be73-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
