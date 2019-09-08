---
title: Koncový bod
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 03c401358839671d750985b95b1aada599931aad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795905"
---
# <a name="endpoint"></a>Koncový bod
Koncový bod  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Třída Endpoint definuje následující metodu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](getoperationcounterinstancename.md)|Načte název instance čítače výkonu operace.|  
  
## <a name="properties"></a>Vlastnosti  
 Třída Endpoint má následující vlastnosti:  
  
### <a name="address"></a>Adresa  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Identifikátor URI, který obsahuje adresu koncového bodu.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Datový typ: pole řetězců  
  
 Typ přístupu: Jen pro čtení  
  
 Kolekce hlaviček adres připojených k tomuto koncovému bodu.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Identita koncového bodu.  
  
### <a name="appdomainid"></a>AppDomainId  
 Datový typ: sint32  
  
 Typ přístupu: Jen pro čtení  
  
 ID domény AppDomain, která hostuje koncový bod.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: Pole chování  
  
 Typ přístupu: Jen pro čtení  
  
 Kolekce chování implementovaná tímto koncovým bodem  
  
### <a name="binding"></a>Vazba  
 Datový typ: Vazba  
  
 Typ přístupu: Jen pro čtení  
  
 Vazba, kterou tento koncový bod používá.  
  
### <a name="contractname"></a>Kontrakt  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Řetězec, který určuje, který kontrakt tento koncový bod vystavuje.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Název instance čítačů výkonu koncového bodu.  
  
### <a name="listenuri"></a>ListenUri  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Identifikátor URI, na kterém je koncový bod naslouchá.  
  
### <a name="name"></a>Name  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Jedinečný název tohoto koncového bodu.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Typ přístupu: Jen pro čtení  
  
 ID procesu, který hostuje koncový bod.  
  
### <a name="ref"></a>ref  
 Datový typ: Kontrakt  
  
 Typ přístupu: Jen pro čtení  
  
 Kontrakt, který tento koncový bod zveřejňuje.  
  
## <a name="requirements"></a>Požadavky  
  
|TVOŘÍCÍ|Deklarováno v souboru ServiceModel. mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definováno v root\ServiceModel|
