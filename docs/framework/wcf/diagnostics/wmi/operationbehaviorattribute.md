---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: d0bf59e6064748a045f761777a2f8f3e88f1cb5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504324"
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
  
 Typ přístupu: jen pro čtení  
  
 Stav funkce automatického dispose pro parametry.  
  
### <a name="impersonation"></a>Zosobnění  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje úroveň představení volajícího, kterou operace podporuje.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Označuje, že když průběhu realizace operace má být objekt.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Označuje, zda aktuální transakce potvrzena automaticky, pokud se nevyskytnou žádné nezpracované výjimky.  
  
### <a name="transactionscoperequired"></a>Vlastností TransactionScopeRequired  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda operace vyžaduje transakci.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.OperationBehaviorAttribute>
