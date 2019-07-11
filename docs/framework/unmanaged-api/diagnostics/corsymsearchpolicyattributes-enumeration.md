---
title: CorSymSearchPolicyAttributes – výčet
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29766636cd151744d25cf66deb60cd2e066e1b32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775776"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="fe0e9-102">CorSymSearchPolicyAttributes – výčet</span><span class="sxs-lookup"><span data-stu-id="fe0e9-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="fe0e9-103">Určuje zásady pro použití při vyhledávání pro modul pro načítání symbolů.</span><span class="sxs-lookup"><span data-stu-id="fe0e9-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="fe0e9-104">Tyto konstanty jsou používány [isymunmanagedbinder2::getreaderforfile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) a [isymunmanagedbinder3::getreaderfromcallback –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fe0e9-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fe0e9-105">To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="fe0e9-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe0e9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe0e9-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="fe0e9-107">Členové</span><span class="sxs-lookup"><span data-stu-id="fe0e9-107">Members</span></span>  
  
|<span data-ttu-id="fe0e9-108">Člen</span><span class="sxs-lookup"><span data-stu-id="fe0e9-108">Member</span></span>|<span data-ttu-id="fe0e9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fe0e9-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="fe0e9-110">Vyhledá v registru cest pro hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="fe0e9-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="fe0e9-111">Přistupuje k serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="fe0e9-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="fe0e9-112">Vyhledá cestě zadané v adresáři ladění.</span><span class="sxs-lookup"><span data-stu-id="fe0e9-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="fe0e9-113">Vyhledá soubor PDB na místě, kde je soubor .exe.</span><span class="sxs-lookup"><span data-stu-id="fe0e9-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe0e9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe0e9-114">Requirements</span></span>  
 <span data-ttu-id="fe0e9-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fe0e9-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0e9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe0e9-116">See also</span></span>

- [<span data-ttu-id="fe0e9-117">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="fe0e9-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
