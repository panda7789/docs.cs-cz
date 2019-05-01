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
ms.openlocfilehash: 8a9b0f085820bac12638c0310ab23b2eafacb23b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986502"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes – výčet
Určuje zásady pro použití při vyhledávání pro modul pro načítání symbolů. Tyto konstanty jsou používány [isymunmanagedbinder2::getreaderforfile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) a [isymunmanagedbinder3::getreaderfromcallback –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) metody.  
  
> [!IMPORTANT]
>  To představuje bezpečnostní riziko pro otevření souboru databáze (PDB) programu z nedůvěryhodného zdroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`AllowRegistryAccess`|Vyhledá v registru cest pro hledání symbolů.|  
|`AllowSymbolServerAccess`|Přistupuje k serveru symbolů.|  
|`AllowOriginalPathAccess`|Vyhledá cestě zadané v adresáři ladění.|  
|`AllowReferencePathAccess`|Vyhledá soubor PDB na místě, kde je soubor .exe.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
