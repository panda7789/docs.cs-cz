---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102931"
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ServiceAuthorizationBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ServiceAuthorizationBehavior má následující vlastnosti:  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, zda se služba pokusí o zosobnění s použitím pověření poskytnutých příchozí zprávy.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Objekt zabezpečení použitý k provádění operací na serveru.  
  
### <a name="roleprovider"></a>RoleProvider  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název poskytovatele rolí prostředí ASP.NET.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Správce autorizace použitý pro autorizace.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
