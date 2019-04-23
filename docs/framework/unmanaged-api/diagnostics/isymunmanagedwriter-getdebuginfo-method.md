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
ms.openlocfilehash: 41d96c6d2024dbc3cab669f2dba2f99faef89f4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074245"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="949d7-102">ISymUnmanagedWriter::GetDebugInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="949d7-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="949d7-103">Vrací informace nezbytné pro kompilátor zapsat záznam adresáře ladění přenosný spustitelný soubor hlavičky souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="949d7-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="949d7-104">Zapisovač symbol vyplní všechna pole s výjimkou `TimeDateStamp` a `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="949d7-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="949d7-105">(Kompilátor je zodpovědný za nastavení těchto dvou polích odpovídajícím způsobem.)</span><span class="sxs-lookup"><span data-stu-id="949d7-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="949d7-106">Kompilátor by měla volat tuto metodu, generování datový objekt blob do souboru PE, nastavte `PointerToRawData` pole IMAGE_DEBUG_DIRECTORY přejděte emitovaný data a zápis IMAGE_DEBUG_DIRECTORY do souboru PE.</span><span class="sxs-lookup"><span data-stu-id="949d7-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="949d7-107">Kompilátor by měl také nastavit `TimeDateStamp` pole tak, aby odpovídal `TimeDateStamp` generování souboru PE.</span><span class="sxs-lookup"><span data-stu-id="949d7-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="949d7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="949d7-108">Syntax</span></span>  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="949d7-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="949d7-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="949d7-110">[out v] Ukazatel na IMAGE_DEBUG_DIRECTORY, který vyplní zapisovač symbol.</span><span class="sxs-lookup"><span data-stu-id="949d7-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="949d7-111">[in] A `DWORD` , který obsahuje množství dat ladění.</span><span class="sxs-lookup"><span data-stu-id="949d7-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="949d7-112">[out] Ukazatel `DWORD` , která obdrží velikost vyrovnávací paměti musí obsahovat data ladění.</span><span class="sxs-lookup"><span data-stu-id="949d7-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="949d7-113">[out] Ukazatel do vyrovnávací paměti, který je dostatečně velký pro uložení data ladění pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="949d7-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="949d7-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="949d7-114">Return Value</span></span>  
 <span data-ttu-id="949d7-115">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="949d7-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="949d7-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="949d7-116">Requirements</span></span>  
 <span data-ttu-id="949d7-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="949d7-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949d7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="949d7-118">See also</span></span>

- [<span data-ttu-id="949d7-119">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="949d7-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
