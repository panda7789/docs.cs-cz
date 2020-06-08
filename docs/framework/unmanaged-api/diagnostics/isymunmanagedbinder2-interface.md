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
ms.openlocfilehash: f6155eb777b5071ff522af4f27d5fb2d73aa25ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501830"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="0a474-102">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a474-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="0a474-103">Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje rozhraní [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0a474-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0a474-104">Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="0a474-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a474-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0a474-105">Methods</span></span>  
  
|<span data-ttu-id="0a474-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a474-106">Method</span></span>|<span data-ttu-id="0a474-107">Description</span><span class="sxs-lookup"><span data-stu-id="0a474-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a474-108">GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="0a474-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="0a474-109">Vzhledem k rozhraní metadat a názvu souboru vrátí správné rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) , které přečte symboly ladění spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="0a474-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="0a474-110">Poskytuje rozsáhlejší hledání než metoda [ISymUnmanagedBinder:: GetReaderForFile –](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0a474-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a474-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a474-111">Requirements</span></span>  
 <span data-ttu-id="0a474-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0a474-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a474-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a474-113">See also</span></span>

- [<span data-ttu-id="0a474-114">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0a474-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0a474-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a474-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="0a474-116">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a474-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
