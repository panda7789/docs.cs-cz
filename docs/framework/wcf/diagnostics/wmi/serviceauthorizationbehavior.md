---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: e03f83927ec5aef7f916b2262c9c8cff1db68ac9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
### <a name="impersonatecallerforalloperations"></a>impersonateCallerForAllOperations  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda se služba pokusí zosobnit pomocí přihlašovacích údajů zadaných příchozí zprávy.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Objekt používá k provádění operací na serveru.  
  
### <a name="roleprovider"></a>RoleProvider  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název poskytovatele rolí prostředí ASP.NET.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Správce autorizací, použít pro vlastní ověřování.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
