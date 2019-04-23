---
title: CorDeclSecurity – výčet
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136965"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity – výčet
Určuje akce zabezpečení, které je možné provádět pomocí deklarativní zabezpečení.  
  
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
|`dclActionMask`|Vyhrazená.|  
|`dclActionNil`|Vyhrazená.|  
|`dclRequest`|Vyhrazená.|  
|`dclDemand`|Všichni volající v zásobníku volání vyšší se vyžadují bylo uděleno oprávnění zadané pomocí aktuálního objektu oprávnění.|  
|`dclAssert`|Volající kód může přístup k prostředku označeném identifikátorem aktuálního objektu oprávnění, i v případě, že volajících výše v zásobníku byla udělena oprávnění pro přístup k prostředku|  
|`dclDeny`|Možnost přístupu k prostředku zadaného parametrem aktuálního objektu oprávnění je odepřen volající, i v případě, že bylo uděleno oprávnění k přístupu.|  
|`dclPermitOnly`|Pouze prostředků zadaných pomocí tohoto oprávnění objektu je možný i v případě, že kód bylo uděleno oprávnění pro přístup k dalším prostředkům.|  
|`dclLinktimeCheck`|Okamžitého volajícího je nutné bylo uděleno oprávnění k zadané pro dané časové období.|  
|`dclInheritanceCheck`|Odvozená třída dědí jiné třídy nebo přepsání metody je potřeba zadané oprávnění udělil.|  
|`dclRequestMinimum`|Volající mohl požadovat pro minimální oprávnění potřebná pro spuštění kódu. Tato akce jde použít jenom v rámci oboru sestavení.|  
|`dclRequestOptional`|Volající mohl požadovat další oprávnění, které jsou volitelné (není vyžadované ke spuštění). Tento požadavek implicitně odmítá všechny další oprávnění, která nejsou výslovně požadována. Tato akce jde použít jenom v rámci oboru sestavení.|  
|`dclRequestRefuse`|Volajícího žádost o oprávnění, která může být potenciálně nebezpečného nebudou udělena. Tato akce jde použít jenom v rámci oboru sestavení.|  
|`dclPrejitGrant`|Vyhrazená.|  
|`dclPrejitDenied`|Vyhrazená.|  
|`dclNonCasDemand`|Vyhrazená.|  
|`dclNonCasLinkDemand`|Okamžitého volajícího je nutné k zadané oprávnění udělil.|  
|`dclNonCasInheritance`|Vyhrazená.|  
|`dclLinkDemandChoice`|Vyhrazená.|  
|`dclInheritanceDemandChoice`|Vyhrazená.|  
|`dclDemandChoice`|Vyhrazená.|  
|`dclMaximumValue`|Vyhrazená.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
