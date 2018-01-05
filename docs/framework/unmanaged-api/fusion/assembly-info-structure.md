---
title: "ASSEMBLY_INFO – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 215d80c3d207c2f50cfbd74386915b0467692b57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO – struktura
Obsahuje informace o sestavení, které je zaregistrován v globální mezipaměti sestavení.  
  
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
|`cbAssemblyInfo`|Velikost v bajtech, struktury. Toto pole je vyhrazený pro budoucí rozšíření.|  
|`dwAssemblyFlags`|Příznaky, které indikují instalace podrobnosti o sestavení. Podporovány jsou následující hodnoty:<br /><br /> Hodnota-ASSEMBLYINFO_FLAG_INSTALLED, která označuje, že je nainstalován sestavení. Aktuální verze rozhraní .NET Framework vždy nastaví `dwAssemblyFlags` na tuto hodnotu.<br />Hodnota-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, která označuje, že je sestavení trvalé datové části. Aktuální verze rozhraní .NET Framework nikdy nastaví `dwAssemblyFlags` na tuto hodnotu.|  
|`uliAssemblySizeInKB`|Celková velikost v kilobajtech, soubory, které obsahuje sestavení.|  
|`pszCurrentAssemblyPathBuf`|Ukazatel na řetězec vyrovnávací paměť, která obsahuje aktuální cestu k souboru manifestu. Cesta musí končit znak hodnoty null.|  
|`cchBuf`|Počet široké znaky, včetně null ukončovací znak, který `pszCurrentAssemblyPathBuf` obsahuje.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Globální mezipaměť sestavení](../../../../docs/framework/app-domains/gac.md)
