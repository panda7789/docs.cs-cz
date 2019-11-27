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
ms.openlocfilehash: 47477bb473df8b568844d07bea704df681c9b95d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448604"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="e1330-102">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1330-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="e1330-103">Poskytuje informace o funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="e1330-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1330-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e1330-104">Methods</span></span>  
  
|<span data-ttu-id="e1330-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e1330-105">Method</span></span>|<span data-ttu-id="e1330-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e1330-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1330-107">GetDocumentsForMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="e1330-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="e1330-108">Načte dokumenty, ve kterých tato metoda obsahuje řádky.</span><span class="sxs-lookup"><span data-stu-id="e1330-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="e1330-109">GetDocumentsForMethodCount – metoda</span><span class="sxs-lookup"><span data-stu-id="e1330-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="e1330-110">Získá počet dokumentů, ve kterých má tato metoda řádky.</span><span class="sxs-lookup"><span data-stu-id="e1330-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="e1330-111">GetFileNameFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e1330-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="e1330-112">Získá název souboru pro řádek přidružený k posunu.</span><span class="sxs-lookup"><span data-stu-id="e1330-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="e1330-113">GetLineFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e1330-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="e1330-114">Získá informace o řádku přidružené k posunu.</span><span class="sxs-lookup"><span data-stu-id="e1330-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="e1330-115">GetSourceExtentInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="e1330-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="e1330-116">Získá nejmenší počáteční řádek a největšího koncového řádku pro metodu v konkrétním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e1330-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1330-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1330-117">Requirements</span></span>  
 <span data-ttu-id="e1330-118">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e1330-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1330-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1330-119">See also</span></span>

- [<span data-ttu-id="e1330-120">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e1330-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
