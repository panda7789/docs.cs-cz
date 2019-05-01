---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: b6221e93f10b87a368bd594932a8c36ae14df8f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957011"
---
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídy ServiceBehaviorAttribute nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídy ServiceBehaviorAttribute má následující vlastnosti:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Označuje, zda automaticky ukončit relaci, když klient ukončí relaci výstupu.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 Datový typ: řetězec  
Typ přístupu: jen pro čtení  
  
 Určuje, zda služba podporuje jedno vlákno, několik vláken nebo znovu zadaných volání.  
  
### <a name="configurationname"></a>ConfigurationName  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název konfigurace služby.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda mají data neznámé serializace přenosu.  
  
### <a name="includeexceptiondetailinfaults"></a>Třídu IncludeExceptionDetailInFaults  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, jestli se má být řízená informace výjimky zařazená do podrobností chyb SOAP vrácena klientům pro účely ladění.  
  
### <a name="instancecontextmode"></a>InstanceContextMode  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, kdy je vytvořen nový objekt služby.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet položek povolených v serializovaném objektu.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Atribut názvu služby ve WSDL.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Cílový obor názvů služby ve WSDL.  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda je objekt služby vrácen, pokud je aktuální transakce dokončena.  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda jsou nevyřízené transakce dokončeny zavře aktuální relaci.  
  
### <a name="transactionisolationlevel"></a>Úroveň TransactionIsolationLevel  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje úroveň izolace transakce.  
  
### <a name="transactiontimeout"></a>Vlastnost TransactionTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Období, ve kterém musí být transakce dokončena.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, jestli se má použít aktuální synchronizační kontext pro výběr provedení vlákna.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda systém nebo aplikace uplatňuje zpracování záhlaví SOAP MustUnderstand.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
