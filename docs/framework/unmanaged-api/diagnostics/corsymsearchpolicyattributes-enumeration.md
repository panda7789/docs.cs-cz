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
ms.openlocfilehash: 5ed868febb5eb82cf73cfc5b0633d86bf4e1315c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561618"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="30f37-102">CorSymSearchPolicyAttributes – výčet</span><span class="sxs-lookup"><span data-stu-id="30f37-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="30f37-103">Určuje zásady pro použití při vyhledávání pro modul pro načítání symbolů.</span><span class="sxs-lookup"><span data-stu-id="30f37-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="30f37-104">Tyto konstanty jsou používány [isymunmanagedbinder2::getreaderforfile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) a [isymunmanagedbinder3::getreaderfromcallback –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="30f37-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="30f37-105">To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="30f37-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f37-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30f37-106">Syntax</span></span>  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="30f37-107">Členové</span><span class="sxs-lookup"><span data-stu-id="30f37-107">Members</span></span>  
  
|<span data-ttu-id="30f37-108">Člen</span><span class="sxs-lookup"><span data-stu-id="30f37-108">Member</span></span>|<span data-ttu-id="30f37-109">Popis</span><span class="sxs-lookup"><span data-stu-id="30f37-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="30f37-110">Vyhledá v registru cest pro hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="30f37-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="30f37-111">Přistupuje k serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="30f37-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="30f37-112">Vyhledá cestě zadané v adresáři ladění.</span><span class="sxs-lookup"><span data-stu-id="30f37-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="30f37-113">Vyhledá soubor PDB na místě, kde je soubor .exe.</span><span class="sxs-lookup"><span data-stu-id="30f37-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30f37-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30f37-114">Requirements</span></span>  
 <span data-ttu-id="30f37-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="30f37-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f37-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30f37-116">See also</span></span>
- [<span data-ttu-id="30f37-117">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="30f37-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
