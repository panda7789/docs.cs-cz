---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 6266713307846ab953299370835726958196fac1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185336"
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída OperationBehaviorAttribute nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída OperationBehaviorAttribute má následující vlastnosti:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Stav funkce automatického dispose pro parametry.  
  
### <a name="impersonation"></a>Zosobnění  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje úroveň představení volajícího, kterou operace podporuje.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode u atributu  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Označuje, že když průběhu realizace operace má být objekt.  
  
### <a name="transactionautocomplete"></a>Vlastnost TransactionAutoComplete  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Označuje, zda aktuální transakce potvrzena automaticky, pokud se nevyskytnou žádné nezpracované výjimky.  
  
### <a name="transactionscoperequired"></a>Vlastností TransactionScopeRequired  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda operace vyžaduje transakci.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
