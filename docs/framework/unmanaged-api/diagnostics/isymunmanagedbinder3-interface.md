---
title: ISymUnmanagedBinder3 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 5a26de2a8f5439b7c81560927c991d449e57b76c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441588"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="b7145-102">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7145-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="b7145-103">Rozšiřuje rozhraní pořadače symbolů.</span><span class="sxs-lookup"><span data-stu-id="b7145-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="b7145-104">Získejte toto rozhraní voláním `QueryInterface` objektu, který implementuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b7145-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b7145-105">Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="b7145-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7145-106">Metody</span><span class="sxs-lookup"><span data-stu-id="b7145-106">Methods</span></span>  
  
|<span data-ttu-id="b7145-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="b7145-107">Method</span></span>|<span data-ttu-id="b7145-108">Popis</span><span class="sxs-lookup"><span data-stu-id="b7145-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7145-109">GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="b7145-109">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="b7145-110">Umožňuje uživateli implementovat nebo dodávkovat prostřednictvím zpětného volání buď `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` , aby získal informace adresáře ladění z paměti.</span><span class="sxs-lookup"><span data-stu-id="b7145-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7145-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7145-111">Requirements</span></span>  
 <span data-ttu-id="b7145-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b7145-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7145-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7145-113">See also</span></span>

- [<span data-ttu-id="b7145-114">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="b7145-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="b7145-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7145-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="b7145-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7145-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
