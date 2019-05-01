---
title: Koncový bod
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 4562481e8b0b18c0ea0d9df0af3427ffe6419821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963602"
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
 Třída koncový bod definuje následující metodu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|Načte název instance čítače výkonu operace|  
  
## <a name="properties"></a>Vlastnosti  
 Třída koncový bod má následující vlastnosti:  
  
### <a name="address"></a>Adresa  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Identifikátor URI, který obsahuje adresu koncového bodu.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Datový typ: pole řetězců  
  
 Typ přístupu: jen pro čtení  
  
 Kolekce záhlaví adres připojených k tomuto koncovému bodu.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Identita koncového bodu.  
  
### <a name="appdomainid"></a>AppDomainId  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Id domény, která hostí koncový bod.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: Chování pole  
  
 Typ přístupu: jen pro čtení  
  
 Kolekce vlastností implementovaná tímto koncovým bodem.  
  
### <a name="binding"></a>Vazba  
 Datový typ: Vazba  
  
 Typ přístupu: jen pro čtení  
  
 Vazba používaný tímto koncovým bodem.  
  
### <a name="contractname"></a>ContractName  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Řetězec, který určuje, jaký kontrakt tento koncový bod vystavuje.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název instance čítače výkonu koncového bodu.  
  
### <a name="listenuri"></a>ListenUri  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Identifikátor Uri koncového bodu naslouchá.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Jedinečný název tohoto koncového bodu.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Proces Id procesu, který je hostitelem koncového bodu.  
  
### <a name="ref"></a>ref  
 Datový typ: Kontrakt  
  
 Typ přístupu: jen pro čtení  
  
 Kontrakt tento koncový bod vystavuje.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|
