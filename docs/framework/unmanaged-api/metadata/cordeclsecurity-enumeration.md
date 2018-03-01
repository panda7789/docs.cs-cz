---
title: "CorDeclSecurity – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30fd7ca2cf7962c6cadb43d4d8e3031b59292463
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity – výčet
Určuje akce zabezpečení, které je možné provést pomocí deklarativních zabezpečení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`dclActionMask`|Vyhrazena.|  
|`dclActionNil`|Vyhrazena.|  
|`dclRequest`|Vyhrazena.|  
|`dclDemand`|Všechny volající vyšší v zásobníku volání je potřeba bylo uděleno oprávnění určeného aktuálního objektu oprávnění.|  
|`dclAssert`|Volání kódu přístup i v případě, že volající vyšší v zásobníku nebylo uděleno oprávnění pro přístup k prostředku v prostředku označeném identifikátorem aktuálního objektu oprávnění|  
|`dclDeny`|Umožňuje přístup k prostředku zadaného parametrem aktuální oprávnění objektu je odepřen volající, i v případě, že bylo uděleno oprávnění k přístupu.|  
|`dclPermitOnly`|Pouze prostředky určeného objektu toto oprávnění lze přistupovat, i v případě, že kód byla udělena oprávnění k přístupu k dalším prostředkům.|  
|`dclLinktimeCheck`|Je potřeba mít nebylo uděleno oprávnění k zadané pro dané časové období bezprostředního volajícího.|  
|`dclInheritanceCheck`|Odvozené třídy dědí jiné třídy nebo přepsání metody je potřeba mít nebylo uděleno oprávnění k zadané.|  
|`dclRequestMinimum`|Volající můžete žádost o minimální oprávnění potřebná pro spuštění kódu. Tuto akci lze použít pouze v rámci oboru sestavení.|  
|`dclRequestOptional`|Volající může požádat o další oprávnění, které jsou volitelné (není požadováno ke spuštění). Tento požadavek implicitně odmítá další oprávnění, které nejsou výslovně požadována. Tuto akci lze použít pouze v rámci oboru sestavení.|  
|`dclRequestRefuse`|Neposkytuje volajícího žádost o oprávnění, která může došlo ke zneužití. Tuto akci lze použít pouze v rámci oboru sestavení.|  
|`dclPrejitGrant`|Vyhrazena.|  
|`dclPrejitDenied`|Vyhrazena.|  
|`dclNonCasDemand`|Vyhrazena.|  
|`dclNonCasLinkDemand`|Je potřeba mít nebylo uděleno oprávnění k zadané bezprostředního volajícího.|  
|`dclNonCasInheritance`|Vyhrazena.|  
|`dclLinkDemandChoice`|Vyhrazena.|  
|`dclInheritanceDemandChoice`|Vyhrazena.|  
|`dclDemandChoice`|Vyhrazena.|  
|`dclMaximumValue`|Vyhrazena.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
