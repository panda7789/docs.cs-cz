---
title: ISymUnmanagedBinder – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7bbdc4b1f15c8dbb154ed7b967bb21c61d11782a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425549"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="321c1-102">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="321c1-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="321c1-103">Představuje vazač symbol pro nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="321c1-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="321c1-104">Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="321c1-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="321c1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="321c1-105">Methods</span></span>  
  
|<span data-ttu-id="321c1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="321c1-106">Method</span></span>|<span data-ttu-id="321c1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="321c1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="321c1-108">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="321c1-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="321c1-109">Vrátí zadaný metadat rozhraní a název souboru správný [ISymUnmanagedReader](isymunmanagedreader-interface.md) struktura, která budou číst související s modulem symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="321c1-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="321c1-110">GetReaderFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="321c1-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="321c1-111">Zadaný datový proud, který obsahuje úložiště symbolů a metadat rozhraní, vrátí správné [ISymUnmanagedReader](isymunmanagedreader-interface.md) struktura, která budou číst ladění symboly z obchodu daný symbol.</span><span class="sxs-lookup"><span data-stu-id="321c1-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="321c1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="321c1-112">Requirements</span></span>  
 <span data-ttu-id="321c1-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="321c1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321c1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="321c1-114">See Also</span></span>  
 [<span data-ttu-id="321c1-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="321c1-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="321c1-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="321c1-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="321c1-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="321c1-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
