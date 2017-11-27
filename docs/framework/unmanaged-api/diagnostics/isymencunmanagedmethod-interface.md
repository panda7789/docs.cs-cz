---
title: "ISymENCUnmanagedMethod – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod
helpviewer_keywords: ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 68929dc30b029133c73f18c3749f39f014359c0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="f00a8-102">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f00a8-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="f00a8-103">Obsahuje informace o funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="f00a8-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f00a8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f00a8-104">Methods</span></span>  
  
|<span data-ttu-id="f00a8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f00a8-105">Method</span></span>|<span data-ttu-id="f00a8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f00a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f00a8-107">Getdocumentsformethod – metoda</span><span class="sxs-lookup"><span data-stu-id="f00a8-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="f00a8-108">Získá dokumenty, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="f00a8-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="f00a8-109">Getdocumentsformethodcount – metoda</span><span class="sxs-lookup"><span data-stu-id="f00a8-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="f00a8-110">Získá počet dokumentů, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="f00a8-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="f00a8-111">Getfilenamefromoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f00a8-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="f00a8-112">Získá název souboru pro přidružené posun řádku.</span><span class="sxs-lookup"><span data-stu-id="f00a8-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="f00a8-113">Getlinefromoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f00a8-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="f00a8-114">Získá související s posunem informace řádku.</span><span class="sxs-lookup"><span data-stu-id="f00a8-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="f00a8-115">Getsourceextentindocument – metoda</span><span class="sxs-lookup"><span data-stu-id="f00a8-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="f00a8-116">Získá spusťte nejmenší číslo řádku a největší na konci řádku pro metodu v konkrétní dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f00a8-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f00a8-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f00a8-117">Requirements</span></span>  
 <span data-ttu-id="f00a8-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f00a8-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f00a8-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f00a8-119">See Also</span></span>  
 [<span data-ttu-id="f00a8-120">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f00a8-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
