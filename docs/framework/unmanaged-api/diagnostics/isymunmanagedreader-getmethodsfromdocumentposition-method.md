---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: bba0fc039c403d45e8a5b60f2b0231eb24226280
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614952"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="241f7-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="241f7-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="241f7-103">Vrátí pole metod, z nichž každý obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="241f7-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="241f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="241f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="241f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="241f7-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="241f7-106">pro Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="241f7-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="241f7-107">pro Řádek zadaného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="241f7-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="241f7-108">pro Sloupec zadaného dokumentu</span><span class="sxs-lookup"><span data-stu-id="241f7-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="241f7-109">pro Velikost `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="241f7-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="241f7-110">mimo Ukazatel na proměnnou, která přijímá počet prvků vrácených v `pRetVal` poli.</span><span class="sxs-lookup"><span data-stu-id="241f7-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="241f7-111">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) , který představuje metodu obsahující zarážku.</span><span class="sxs-lookup"><span data-stu-id="241f7-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="241f7-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="241f7-112">Return Value</span></span>  
 <span data-ttu-id="241f7-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="241f7-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="241f7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="241f7-114">Requirements</span></span>  
 <span data-ttu-id="241f7-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="241f7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="241f7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="241f7-116">See also</span></span>

- [<span data-ttu-id="241f7-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="241f7-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
