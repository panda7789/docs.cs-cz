---
title: ISymENCUnmanagedMethod – rozhraní
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4474269688094ea6c81b06659727acfb9c2ad6c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940254"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="1a991-102">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a991-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="1a991-103">Obsahuje informace o funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="1a991-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a991-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1a991-104">Methods</span></span>  
  
|<span data-ttu-id="1a991-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1a991-105">Method</span></span>|<span data-ttu-id="1a991-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1a991-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a991-107">GetDocumentsForMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="1a991-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="1a991-108">Získá dokumenty, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="1a991-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="1a991-109">GetDocumentsForMethodCount – metoda</span><span class="sxs-lookup"><span data-stu-id="1a991-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="1a991-110">Získá počet dokumentů, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="1a991-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="1a991-111">GetFileNameFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="1a991-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="1a991-112">Získá název souboru pro řádek spojený s posunem.</span><span class="sxs-lookup"><span data-stu-id="1a991-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="1a991-113">GetLineFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="1a991-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="1a991-114">Získá informace o řádku, které jsou spojené s posunem.</span><span class="sxs-lookup"><span data-stu-id="1a991-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="1a991-115">GetSourceExtentInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="1a991-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="1a991-116">Získá spuštění nejmenší číslo řádku a největší na konci řádku pro metodu v určitého dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1a991-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a991-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a991-117">Requirements</span></span>  
 <span data-ttu-id="1a991-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1a991-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a991-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a991-119">See also</span></span>

- [<span data-ttu-id="1a991-120">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="1a991-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
