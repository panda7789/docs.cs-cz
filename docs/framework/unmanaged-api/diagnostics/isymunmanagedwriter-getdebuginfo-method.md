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
ms.openlocfilehash: f8eb4cb6bad95295e10a72812fa8dbb0adfcc898
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614783"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="915ff-102">ISymUnmanagedWriter::GetDebugInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="915ff-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="915ff-103">Vrátí informace, které jsou nezbytné pro kompilátor pro zápis položky adresáře ladění v hlavičce přenositelného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="915ff-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="915ff-104">Zapisovač symbolů vyplní všechna pole s výjimkou `TimeDateStamp` a `PointerToRawData` .</span><span class="sxs-lookup"><span data-stu-id="915ff-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="915ff-105">(Kompilátor je zodpovědný za správné nastavení těchto dvou polí.)</span><span class="sxs-lookup"><span data-stu-id="915ff-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="915ff-106">Kompilátor by měl zavolat tuto metodu, vygenerovat datový objekt blob do souboru PE, nastavit `PointerToRawData` pole v IMAGE_DEBUG_DIRECTORY tak, aby odkazovalo na emitovaná data, a zapsat IMAGE_DEBUG_DIRECTORY do souboru PE.</span><span class="sxs-lookup"><span data-stu-id="915ff-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="915ff-107">Kompilátor by měl také nastavit `TimeDateStamp` pole tak, aby se rovnalo `TimeDateStamp` vygenerovanému souboru PE.</span><span class="sxs-lookup"><span data-stu-id="915ff-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915ff-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="915ff-108">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="915ff-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="915ff-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="915ff-110">[in, out] Ukazatel na IMAGE_DEBUG_DIRECTORY, který zapisovač symbolů vyplní.</span><span class="sxs-lookup"><span data-stu-id="915ff-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="915ff-111">pro A `DWORD` který obsahuje velikost ladicích dat.</span><span class="sxs-lookup"><span data-stu-id="915ff-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="915ff-112">mimo Ukazatel na `DWORD` , který přijímá velikost vyrovnávací paměti, která je nutná k uložení ladicích dat.</span><span class="sxs-lookup"><span data-stu-id="915ff-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="915ff-113">mimo Ukazatel na vyrovnávací paměť, která je dostatečně velká pro ukládání dat ladění pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="915ff-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="915ff-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="915ff-114">Return Value</span></span>  
 <span data-ttu-id="915ff-115">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="915ff-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915ff-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="915ff-116">Requirements</span></span>  
 <span data-ttu-id="915ff-117">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="915ff-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915ff-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="915ff-118">See also</span></span>

- [<span data-ttu-id="915ff-119">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="915ff-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
