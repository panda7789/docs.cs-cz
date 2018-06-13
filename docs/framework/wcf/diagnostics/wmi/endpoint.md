---
title: Koncový bod
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 5d597e9e029cec3552c94b47a64dfbf36d933e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487643"
---
# <a name="endpoint"></a>Koncový bod
Koncový bod  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída koncový bod definuje následující metodu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|Načte název instance čítače výkonu operace|  
  
## <a name="properties"></a>Vlastnosti  
 Třída koncový bod má následující vlastnosti:  
  
### <a name="address"></a>Adresa  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Identifikátor URI, který obsahuje adresu koncového bodu.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Datový typ: pole řetězců  
  
 Přístup k typu: jen pro čtení  
  
 Kolekce hlavičky adresy, které jsou připojené k tomuto koncovému bodu.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Identitu koncového bodu.  
  
### <a name="appdomainid"></a>AppDomainId  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Identifikační číslo domény, který je hostitelem koncového bodu.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: chování pole  
  
 Přístup k typu: jen pro čtení  
  
 Kolekce vlastností implementovaná tento koncový bod.  
  
### <a name="binding"></a>Vazba  
 Datový typ: vytvoření vazby  
  
 Přístup k typu: jen pro čtení  
  
 Vazba používaný tímto koncovým bodem.  
  
### <a name="contractname"></a>ContractName  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Řetězec, který určuje, jaký kontrakt tento koncový bod je vystavení.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název instance čítače výkonu koncového bodu.  
  
### <a name="listenuri"></a>Adrese ListenUri  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Identifikátor Uri koncového bodu naslouchá na.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Jedinečný název tohoto koncového bodu.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Id procesu, který je hostitelem koncového bodu procesu.  
  
### <a name="ref"></a>ref  
 Datový typ: kontraktu  
  
 Přístup k typu: jen pro čtení  
  
 Kontrakt tento koncový bod je vystavení.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|
