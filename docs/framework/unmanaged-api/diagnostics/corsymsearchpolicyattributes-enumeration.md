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
ms.openlocfilehash: 4fd31e6b752e13a5c43198760e9a4d62a8f77d10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448560"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes – výčet
Určuje zásadu, která se má použít při hledání čtečky symbolů. Tyto konstanty jsou používány metodami [ISymUnmanagedBinder2 –:: GetReaderForFile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) a [Isymunmanagedbinder3 –:: GetReaderFromCallback –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) .  
  
> [!IMPORTANT]
> Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`AllowRegistryAccess`|Vyhledá v registru cesty pro hledání symbolů.|  
|`AllowSymbolServerAccess`|Přistupuje k serveru symbolů.|  
|`AllowOriginalPathAccess`|Vyhledá cestu zadanou v adresáři ladění.|  
|`AllowReferencePathAccess`|Vyhledá PDB na místě, kde se nachází soubor. exe.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
