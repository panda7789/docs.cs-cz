---
title: ISymUnmanagedBinder2 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: 8a4fbb40ec2426d000628fbd6d5f0241d3152c18
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441666"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="fb1f3-102">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb1f3-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="fb1f3-103">Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje rozhraní [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fb1f3-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fb1f3-104">Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="fb1f3-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb1f3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fb1f3-105">Methods</span></span>  
  
|<span data-ttu-id="fb1f3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fb1f3-106">Method</span></span>|<span data-ttu-id="fb1f3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fb1f3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb1f3-108">GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fb1f3-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="fb1f3-109">Vzhledem k rozhraní metadat a názvu souboru vrátí správné rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) , které přečte symboly ladění spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="fb1f3-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="fb1f3-110">Poskytuje rozsáhlejší hledání než metoda [ISymUnmanagedBinder:: GetReaderForFile –](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fb1f3-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb1f3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb1f3-111">Requirements</span></span>  
 <span data-ttu-id="fb1f3-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fb1f3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1f3-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb1f3-113">See also</span></span>

- [<span data-ttu-id="fb1f3-114">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="fb1f3-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="fb1f3-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb1f3-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="fb1f3-116">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb1f3-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
