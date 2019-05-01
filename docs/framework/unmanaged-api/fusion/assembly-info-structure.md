---
title: ASSEMBLY_INFO – struktura
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985956"
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO – struktura
Obsahuje informace o sestavení, který je zaregistrován v globální mezipaměti sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`cbAssemblyInfo`|Velikost v bajtech struktury. Toto pole je vyhrazený pro budoucí rozšíření.|  
|`dwAssemblyFlags`|Příznaky, které označují podrobné informace o instalaci o sestavení. Podporovány jsou následující hodnoty:<br /><br /> -ASSEMBLYINFO_FLAG_INSTALLED hodnotu, která označuje, že je nainstalována sestavení. Aktuální verze rozhraní .NET Framework vždy nastavuje `dwAssemblyFlags` na tuto hodnotu.<br />-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT hodnotu, která označuje, že je sestavení rezidenční datovou část. Aktuální verze rozhraní .NET Framework nikdy nastaví `dwAssemblyFlags` na tuto hodnotu.|  
|`uliAssemblySizeInKB`|Celková velikost v kilobajtech, soubory, které obsahuje sestavení.|  
|`pszCurrentAssemblyPathBuf`|Ukazatel do vyrovnávací paměti pro řetězec, který obsahuje aktuální cesta k souboru manifestu. Cesta musí být ukončen znakem null.|  
|`cchBuf`|Počet širokých znaků, včetně ukončovacího znaku null, který `pszCurrentAssemblyPathBuf` obsahuje.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Globální mezipaměť sestavení](../../../../docs/framework/app-domains/gac.md)
