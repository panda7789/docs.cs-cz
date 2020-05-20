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
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441874"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="57e2a-102">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57e2a-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="57e2a-103">Poskytuje informace o funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="57e2a-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57e2a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="57e2a-104">Methods</span></span>  
  
|<span data-ttu-id="57e2a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="57e2a-105">Method</span></span>|<span data-ttu-id="57e2a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="57e2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57e2a-107">GetDocumentsForMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="57e2a-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="57e2a-108">Načte dokumenty, ve kterých tato metoda obsahuje řádky.</span><span class="sxs-lookup"><span data-stu-id="57e2a-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="57e2a-109">GetDocumentsForMethodCount – metoda</span><span class="sxs-lookup"><span data-stu-id="57e2a-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="57e2a-110">Získá počet dokumentů, ve kterých má tato metoda řádky.</span><span class="sxs-lookup"><span data-stu-id="57e2a-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="57e2a-111">GetFileNameFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="57e2a-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="57e2a-112">Získá název souboru pro řádek přidružený k posunu.</span><span class="sxs-lookup"><span data-stu-id="57e2a-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="57e2a-113">GetLineFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="57e2a-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="57e2a-114">Získá informace o řádku přidružené k posunu.</span><span class="sxs-lookup"><span data-stu-id="57e2a-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="57e2a-115">GetSourceExtentInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="57e2a-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="57e2a-116">Získá nejmenší počáteční řádek a největšího koncového řádku pro metodu v konkrétním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="57e2a-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57e2a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57e2a-117">Requirements</span></span>  
 <span data-ttu-id="57e2a-118">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="57e2a-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e2a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="57e2a-119">See also</span></span>

- [<span data-ttu-id="57e2a-120">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="57e2a-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
